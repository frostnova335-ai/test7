import React, { useCallback, useEffect, useMemo, useState } from 'react';
import { PlayCircleOutlined, PauseCircleOutlined } from '@ant-design/icons';
import { t } from '@superset-ui/core';

const playButtonStyle: React.CSSProperties = {
  cursor: 'pointer',
  display: 'inline-flex',
  alignItems: 'center',
  color: '#2893B3',
  fontSize: 20,
};

interface PlayButtonProps {
  audioUrl: string | null;
  title?: string;
}

let globalAudio: HTMLAudioElement | null = null;
let globalAudioSrc: string | null = null;
let listeners: Array<() => void> = [];

function notifyListeners() {
  listeners.forEach(listener => listener());
}

function ensureGlobalAudio(): HTMLAudioElement {
  if (globalAudio) {
    return globalAudio;
  }
  globalAudio = new Audio();
  globalAudio.preload = 'none';
  globalAudio.addEventListener('play', notifyListeners);
  globalAudio.addEventListener('pause', notifyListeners);
  globalAudio.addEventListener('ended', notifyListeners);
  globalAudio.addEventListener('error', notifyListeners);
  globalAudio.addEventListener('waiting', notifyListeners);
  globalAudio.addEventListener('canplay', notifyListeners);
  return globalAudio;
}

function subscribe(listener: () => void): () => void {
  listeners.push(listener);
  return () => {
    listeners = listeners.filter(entry => entry !== listener);
  };
}

function normalizeUrl(url: string): string {
  try {
    const parsed = new URL(url, window.location.origin);
    return `${parsed.origin}${parsed.pathname}`;
  } catch {
    return url.trim();
  }
}

/**
 * Build absolute URL for reliable loading (e.g. when app is behind proxy).
 */
function toAbsoluteUrl(audioUrl: string): string {
  try {
    if (audioUrl.startsWith('http://') || audioUrl.startsWith('https://')) {
      return audioUrl;
    }
    return new URL(audioUrl, window.location.origin).href;
  } catch {
    return '';
  }
}

function safePlay(audio: HTMLAudioElement) {
  const playPromise = audio.play();
  if (playPromise && typeof playPromise.catch === 'function') {
    playPromise.catch(() => {
      // no-op: absorb async playback errors (e.g. missing/unsupported source)
      // so they do not surface as unhandled runtime errors.
    });
  }
}

/**
 * Play button backed by a shared HTMLAudioElement so only one row plays at a time.
 */
export default function PlayButton({ audioUrl, title }: PlayButtonProps) {
  const [, setVersion] = useState(0);

  useEffect(
    () =>
      subscribe(() => {
        setVersion(version => version + 1);
      }),
    [],
  );


  const absoluteUrl = useMemo(() => {
    if (!audioUrl || typeof audioUrl !== 'string' || !audioUrl.trim()) {
      return null;
    }

    const resolvedUrl = toAbsoluteUrl(audioUrl.trim());
    return resolvedUrl || null;
  }, [audioUrl]);

  const audio = globalAudio;
  const isCurrentSource =
    absoluteUrl !== null &&
    typeof globalAudioSrc === 'string' &&
    normalizeUrl(globalAudioSrc) === normalizeUrl(absoluteUrl);
  const isThisPlaying = isCurrentSource && !!audio && !audio.paused;
  const isLoading =
    isCurrentSource &&
    !!audio &&
    audio.readyState < HTMLMediaElement.HAVE_FUTURE_DATA;
  const hasError = isCurrentSource && !!audio && audio.error != null;

  const handleClick = useCallback(
    (e?: React.MouseEvent | React.KeyboardEvent) => {
      e?.stopPropagation();
      e?.preventDefault();

      if (!absoluteUrl) return;

      try {
        const nextAudio = ensureGlobalAudio();
        if (isCurrentSource) {
          if (nextAudio.paused) {
            safePlay(nextAudio);
          } else {
            nextAudio.pause();
          }
        } else {
          nextAudio.pause();
          nextAudio.src = absoluteUrl;
          globalAudioSrc = absoluteUrl;
          safePlay(nextAudio);
          notifyListeners();
        }
      } catch {
        // no-op: avoid crashing chart render if media playback fails.
      }
    },
    [absoluteUrl, isCurrentSource],
  );

  if (!absoluteUrl) {
    return <span aria-hidden>-</span>;
  }

  const icon = isThisPlaying ? (
    <PauseCircleOutlined aria-label={t('Pause')} />
  ) : (
    <PlayCircleOutlined aria-label={t('Play')} />
  );

  const tooltipText = title || (isThisPlaying ? t('Pause') : t('Play'));

  return (
    <span
      role="button"
      tabIndex={0}
      style={playButtonStyle}
      title={hasError ? undefined : tooltipText}
      onClick={e => handleClick(e)}
      onKeyDown={e => {
        if (e.key === 'Enter' || e.key === ' ') {
          handleClick(e);
        }
      }}
    >
      {isLoading && isCurrentSource ? (
        <span style={{ fontSize: 18 }} aria-label={t('Loading')}>
          ...
        </span>
      ) : (
        icon
      )}
    </span>
  );
}





import { t } from '@superset-ui/core';
import {
  ControlPanelConfig,
  getStandardizedControls,
  sharedControls,
} from '@superset-ui/chart-controls';

export const controlPanel: ControlPanelConfig = {
  controlPanelSections: [
    {
      label: t('Query'),
      expanded: true,
      controlSetRows: [
        [
          {
            name: 'groupby',
            config: {
              ...sharedControls.groupby,
              label: t('Columns'),
              description: t('Columns to display in the table'),
              default: [],
            },
          },
        ],
        ['adhoc_filters'],
        ['row_limit'],
        [
          {
            name: 'audio_column',
            config: {
              type: 'SelectControl',
              label: t('Audio column'),
              description: t(
                'Column that contains the audio filename (e.g. welcome.mp3). ' +
                  'Files are loaded from the common audio folder.',
              ),
              default: null,
              mapStateToProps: ({ datasource }) => ({
                choices: (datasource?.columns || []).map(
                  (col: { column_name: string; verbose_name?: string }) =>
                    [col.column_name, col.verbose_name || col.column_name],
                ),
              }),
              freeForm: false,
            },
          },
        ],
        [
          {
            name: 'audio_base_path',
            config: {
              type: 'TextControl',
              label: t('Audio base path'),
              description: t(
                'Base URL/path for audio files. Default: /static/assets/common-audio/',
              ),
              default: '/static/assets/common-audio/',
            },
          },
        ],
      ],
    },
  ],
  formDataOverrides: formData => {
    const selectedColumns = getStandardizedControls().popAllColumns();
    const extractColumnName = (raw: unknown): string | null => {
      if (typeof raw === 'string') return raw;
      if (Array.isArray(raw) && raw.length > 0) return extractColumnName(raw[0]);
      if (typeof raw === 'object' && raw !== null) {
        const obj = raw as {
          value?: unknown;
          column_name?: unknown;
          label?: unknown;
        };
        if (typeof obj.column_name === 'string') return obj.column_name;
        if (typeof obj.value === 'string') return obj.value;
        if (obj.value != null) return extractColumnName(obj.value);
        if (typeof obj.label === 'string') return obj.label;
      }
      return null;
    };
    const audioColumn = extractColumnName(formData.audio_column);
    const allColumns =
      audioColumn && !selectedColumns.includes(audioColumn)
        ? [...selectedColumns, audioColumn]
        : selectedColumns;

    return {
      ...formData,
      // Always include configured Audio column in payload even if not shown as a display column.
      query_mode: 'raw',
      all_columns: allColumns,
      // Compatibility fallback for query builders that ignore raw mode.
      groupby: allColumns,
      metrics: [],
      metric: null,
      percent_metrics: [],
      granularity_sqla: null,
      granularity: null,
      time_grain_sqla: null,
      timeseries_limit_metric: null,
      order_desc: null,
      orderby: null,
    };
  },
};


export { controlPanel } from './controlPanel';
export { transformProps } from './transformProps';


import { DataRecord } from '@superset-ui/core';
import type { AudioTableProps } from '../types';

interface QueryData {
  data?: DataRecord[] | { records?: DataRecord[]; columns?: string[] };
  records?: DataRecord[];
  colnames?: string[] | { column_name: string }[];
  columns?: string[] | { column_name: string }[];
  form_data?: FormData;
}

interface FormData {
  audio_column?: unknown;
  audio_base_path?: string;
  groupby?: unknown;
  all_columns?: unknown;
  slice_id?: number;
}

export interface AudioTableChartProps {
  height?: number;
  width?: number;
  formData?: FormData;
  queriesData?: QueryData[];
}

const AUDIO_EXTENSIONS = /\.(mp3|wav|m4a|aac|ogg|flac|webm)(\?.*)?$/i;

function isLikelyAudioValue(value: unknown): boolean {
  if (value == null) return false;

  const normalized = (() => {
    if (typeof value === 'string' || typeof value === 'number') {
      return String(value).trim();
    }
    if (typeof value === 'object' && value !== null && 'value' in value) {
      const nested = (value as { value?: unknown }).value;
      return nested == null ? '' : String(nested).trim();
    }
    return String(value).trim();
  })();

  if (!normalized) return false;
  if (AUDIO_EXTENSIONS.test(normalized)) return true;
  if (/^https?:\/\//i.test(normalized) && AUDIO_EXTENSIONS.test(normalized)) {
    return true;
  }

  return false;
}

function inferAudioColumnFromData(
  columnNames: string[],
  records: DataRecord[],
): string | null {
  if (columnNames.length === 0 || records.length === 0) return null;

  const sampleRows = records.slice(0, Math.min(records.length, 50));
  let bestColumn: string | null = null;
  let bestScore = 0;

  columnNames.forEach(columnName => {
    const score = sampleRows.reduce((count, row) => {
      const value = row[columnName];
      return count + (isLikelyAudioValue(value) ? 1 : 0);
    }, 0);

    if (score > bestScore) {
      bestScore = score;
      bestColumn = columnName;
    }
  });

  return bestScore > 0 ? bestColumn : null;
}

function getRecordKeys(records: DataRecord[]): string[] {
  if (records.length === 0) {
    return [];
  }
  const keySet = new Set<string>();
  records.slice(0, Math.min(records.length, 50)).forEach(row => {
    Object.keys(row || {}).forEach(key => keySet.add(key));
  });
  return Array.from(keySet);
}

function resolveColumnKey(
  requestedColumn: string | null,
  columnNames: string[],
  recordKeys: string[],
): string | null {
  if (!requestedColumn) {
    return null;
  }
  if (columnNames.includes(requestedColumn)) {
    return requestedColumn;
  }
  if (recordKeys.includes(requestedColumn)) {
    return requestedColumn;
  }

  const requestedLower = requestedColumn.toLowerCase();
  const caseInsensitiveMatch =
    columnNames.find(col => col.toLowerCase() === requestedLower) ||
    recordKeys.find(col => col.toLowerCase() === requestedLower);

  return caseInsensitiveMatch || null;
}

function extractGroupbyColumns(rawGroupby: unknown): string[] {
  if (!Array.isArray(rawGroupby)) {
    return [];
  }
  return rawGroupby
    .map(item => {
      if (typeof item === 'string') return item;
      if (typeof item === 'object' && item !== null) {
        const value = (item as { column_name?: unknown; value?: unknown })
          .column_name;
        if (typeof value === 'string') return value;
        const altValue = (item as { value?: unknown }).value;
        if (typeof altValue === 'string') return altValue;
      }
      return null;
    })
    .filter((item): item is string => typeof item === 'string');
}

function extractAllColumns(rawColumns: unknown): string[] {
  if (!Array.isArray(rawColumns)) {
    return [];
  }
  return rawColumns
    .map(item => {
      if (typeof item === 'string') return item;
      if (typeof item === 'object' && item !== null) {
        const obj = item as {
          column_name?: unknown;
          value?: unknown;
          label?: unknown;
        };
        if (typeof obj.column_name === 'string') return obj.column_name;
        if (typeof obj.value === 'string') return obj.value;
        if (typeof obj.label === 'string') return obj.label;
      }
      return null;
    })
    .filter((item): item is string => typeof item === 'string');
}

function extractColumnName(raw: unknown): string | null {
  if (raw == null || raw === '') return null;
  if (typeof raw === 'string') return raw;
  if (Array.isArray(raw) && raw.length > 0) {
    return extractColumnName(raw[0]);
  }
  if (typeof raw === 'object' && raw !== null) {
    const obj = raw as {
      value?: unknown;
      column_name?: unknown;
      label?: unknown;
    };
    if (typeof obj.column_name === 'string') return obj.column_name;
    if (typeof obj.value === 'string') return obj.value;
    if (obj.value != null) return extractColumnName(obj.value);
    if (typeof obj.label === 'string') return obj.label;
  }
  return null;
}

export function transformProps(chartProps: AudioTableChartProps): AudioTableProps {
  const { height = 400, width, formData: formDataProp, queriesData } = chartProps;
  // Legacy API returns full payload as first item: { data, colnames, form_data, ... }
  const payload = queriesData[0] ?? {};
  const rawRecords = payload?.data ?? payload?.records ?? [];
  const records =
    Array.isArray(rawRecords)
      ? rawRecords
      : Array.isArray((rawRecords as { records?: DataRecord[] })?.records)
        ? (rawRecords as { records: DataRecord[] }).records
        : [];
  const columns = payload?.colnames ?? payload?.columns ?? [];
  // payload.form_data is tied to the executed query and is often the latest.
  // Merge with chartProps.formData to avoid dropping values in either source.
  const payloadFormData = (
    payload as { form_data?: { audio_column?: unknown; audio_base_path?: string } }
  ).form_data ?? {};
  const formData = {
    ...payloadFormData,
    ...(formDataProp ?? {}),
  };
  const selectedColumns = (() => {
    const fromGroupby = extractGroupbyColumns(formData.groupby);
    if (fromGroupby.length > 0) {
      return fromGroupby;
    }
    return extractAllColumns(formData.all_columns);
  })();

  // Ensure columns is string[] (backend may return { column_name, id }[])
  const columnNames = columns.map((c: string | { column_name: string }) =>
    typeof c === 'string' ? c : (c as { column_name: string }).column_name,
  );
  const recordKeys = getRecordKeys(records);

  // Extract column name: SelectControl may store {value, label} object
  const audioColName = extractColumnName(formData.audio_column);

  let audioColumnKey = resolveColumnKey(audioColName, columnNames, recordKeys);

  // Fallback: if no audio column configured (e.g. chart saved before setting),
  // auto-detect common audio column names
  if (!audioColumnKey && columnNames.length > 0) {
    const audioLikeColumns = [
      'audio_url',
      'audio_uri',
      'audio_file',
      'audiofile',
      'audio',
      'sound_file',
      'file',
    ];
    const availableColumns = Array.from(new Set([...columnNames, ...recordKeys]));
    const lowerToOriginal = new Map(
      availableColumns.map(col => [col.toLowerCase(), col] as const),
    );
    const matched = audioLikeColumns.find(col =>
      lowerToOriginal.has(col.toLowerCase()),
    );
    audioColumnKey = matched ? lowerToOriginal.get(matched.toLowerCase()) ?? null : null;
  }

  // Last fallback: infer the most likely audio column by inspecting sample row values.
  if (!audioColumnKey) {
    const availableColumns = Array.from(new Set([...columnNames, ...recordKeys]));
    audioColumnKey = inferAudioColumnFromData(availableColumns, records);
  }

  const audioBasePath =
    formData.audio_base_path?.trim() || '/static/assets/common-audio/';
  const displayColumns =
    selectedColumns.length > 0
      ? selectedColumns.filter(column =>
          Array.from(new Set([...columnNames, ...recordKeys])).includes(column),
        )
      : columnNames.filter(column => column !== audioColumnKey);
  const visibleColumns =
    audioColumnKey == null
      ? displayColumns
      : displayColumns.filter(column => column !== audioColumnKey);

  return {
    height,
    width,
    data: records,
    columns: visibleColumns,
    audioColumnKey,
    audioBasePath,
    sliceId:
      typeof formData.slice_id === 'number' ? formData.slice_id : null,
  };
}





import { useMemo, useState } from 'react';
import { TableView } from '@superset-ui/core/components';
import { styled, t } from '@superset-ui/core';
import type { AudioTableProps } from './types';
import PlayButton from './components/PlayButton';
import HeaderSearchPortal from '../components/HeaderSearchPortal';

const AUDIO_PLAY_COLUMN_ID = '__audio_play__';
const DEFAULT_AUDIO_BASE_PATH = '/static/assets/common-audio/';

const AudioTableStyles = styled.div<{ height?: number }>`
  height: ${props => props.height}px;
  overflow: auto;

  .table-no-hover {
    width: 100%;
  }
`;

/**
 * Extract primitive value from cell data. Backend may return {value, label} objects
 * for select/enum columns; React cannot render objects as children.
 */
function toPrimitive(value: unknown): string | number | null {
  if (value == null || value === '') {
    return null;
  }
  if (typeof value === 'object' && value !== null && 'value' in value) {
    const obj = value as { value?: unknown };
    return obj.value != null ? toPrimitive(obj.value) : null;
  }
  if (typeof value === 'object' && value !== null && 'label' in value) {
    const obj = value as { label?: unknown };
    return obj.label != null ? toPrimitive(obj.label) : null;
  }
  if (typeof value === 'string' || typeof value === 'number') {
    return value;
  }
  return String(value);
}

/**
 * Build audio URL from base path and filename.
 * Supports: filename only (e.g. "welcome.mp3"), relative path, or full URL.
 */
function getAudioUrl(value: unknown, basePath: string): string | null {
  const prim = toPrimitive(value);
  if (prim == null || prim === '') return null;
  const str = String(prim).trim();
  if (!str) return null;

  // Full URL - use as-is
  if (str.startsWith('http://') || str.startsWith('https://')) {
    return str;
  }

  // Absolute path - prepend window origin if needed
  if (str.startsWith('/')) {
    return str;
  }

  // Filename or relative path - prepend base path
  const base = basePath.endsWith('/') ? basePath : `${basePath}/`;
  return base + str;
}

function AudioTableContent({
  className = '',
  height = 400,
  data,
  columns,
  audioColumnKey,
  audioBasePath = DEFAULT_AUDIO_BASE_PATH,
  sliceId,
}: AudioTableProps) {
  const [searchText, setSearchText] = useState('');

  const normalizedSearch = searchText.trim().toLowerCase();

  const filteredData = useMemo(() => {
    if (!normalizedSearch) {
      return data;
    }
    return data.filter(row =>
      columns.some(col => {
        const value = toPrimitive(row[col]);
        if (value == null) return false;
        return String(value).toLowerCase().includes(normalizedSearch);
      }),
    );
  }, [columns, data, normalizedSearch]);

  const tableColumns = useMemo(() => {
    const dataColumns = columns.map(col => ({
      accessor: col,
      Header: col,
      id: col,
    }));

    const playColumn = {
      accessor: AUDIO_PLAY_COLUMN_ID,
      Header: t('Play'),
      id: AUDIO_PLAY_COLUMN_ID,
      disableSortBy: true,
      width: 60,
    };

    return [...dataColumns, playColumn];
  }, [columns]);

  const tableData = useMemo(() => {
    return filteredData.map(row => {
      const cells: Record<string, unknown> = {};
      columns.forEach(col => {
        const val = row[col];
        cells[col] = toPrimitive(val) ?? '';
      });
      const audioValue = audioColumnKey ? row[audioColumnKey] : null;
      const audioUrl = getAudioUrl(audioValue, audioBasePath);
      cells[AUDIO_PLAY_COLUMN_ID] = (
        <PlayButton audioUrl={audioUrl} title={t('Play audio')} />
      );
      return cells;
    });
  }, [filteredData, columns, audioColumnKey, audioBasePath]);

  return (
    <AudioTableStyles
      data-test="audio-table"
      className={className}
      height={height}
    >
      <HeaderSearchPortal
        sliceId={sliceId}
        count={data.length}
        value={searchText}
        onChange={setSearchText}
      />
      <TableView
        className="table-no-hover"
        columns={tableColumns}
        data={tableData}
        withPagination={filteredData.length > 10}
        pageSize={10}
      />
    </AudioTableStyles>
  );
}

export default function AudioTable(props: AudioTableProps) {
  return <AudioTableContent {...props} />;
}





import { t, ChartMetadata, ChartPlugin } from '@superset-ui/core';
import { transformProps, controlPanel } from './config';
// Reuse Table chart thumbnail (audio table is table-like)
import thumbnail from '../../../plugins/plugin-chart-table/src/images/thumbnail.png';
import thumbnailDark from '../../../plugins/plugin-chart-table/src/images/thumbnail-dark.png';

const metadata = new ChartMetadata({
  category: t('Table'),
  name: t('Audio Table'),
  description: t(
    'Table with an audio Play column. Add a column containing audio filenames (e.g. welcome.mp3) ' +
      'and select it as the audio column. Files load from the common audio folder.',
  ),
  tags: [
    t('Tabular'),
    t('Audio'),
  ],
  thumbnail,
  thumbnailDark,
  useLegacyApi: true,
});

export default class AudioTableChartPlugin extends ChartPlugin {
  constructor() {
    super({
      metadata,
      transformProps,
      loadChart: () => import('./AudioTable'),
      controlPanel,
    });
  }
}




import { DataRecord } from '@superset-ui/core';

export interface AudioTableProps {
  className?: string;
  height?: number;
  width?: number;
  data: DataRecord[];
  columns: string[];
  audioColumnKey: string | null;
  audioBasePath?: string;
  sliceId?: number | null;
}
