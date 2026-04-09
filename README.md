import { useMemo, useState, useEffect, useRef } from 'react';
import { TableView } from '@superset-ui/core/components';
import { styled, t } from '@superset-ui/core';
import type { AudioTableProps } from './types';
import PlayButton from './components/PlayButton';
import HeaderSearchPortal from '../components/HeaderSearchPortal';
import WaveSurfer from 'wavesurfer.js';
 
const AUDIO_PLAY_COLUMN_ID = '__audio_play__';
const DEFAULT_AUDIO_BASE_PATH = '/static/assets/common-audio/';
 
const AudioTableStyles = styled.div<{ height?: number }>`
  height: ${props => props.height}px;
  overflow: auto;
 
  .table-no-hover {
    width: 100%;
  }
`;
 
function toPrimitive(value: unknown): string | number | null {
  if (value == null || value === '') return null;
 
  if (typeof value === 'object' && value !== null && 'value' in value) {
    const obj = value as { value?: unknown };
    return obj.value != null ? toPrimitive(obj.value) : null;
  }
 
  if (typeof value === 'object' && value !== null && 'label' in value) {
    const obj = value as { label?: unknown };
    return obj.label != null ? toPrimitive(obj.label) : null;
  }
 
  if (typeof value === 'string' || typeof value === 'number') return value;
 
  return String(value);
}
 
function getAudioUrl(value: unknown, basePath: string): string | null {
  const prim = toPrimitive(value);
  if (prim == null || prim === '') return null;
 
  const str = String(prim).trim();
  if (!str) return null;
 
  if (str.startsWith('http://') || str.startsWith('https://')) return str;
 
  if (str.startsWith('/')) return str;
 
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
 
  const waveformRef = useRef<HTMLDivElement | null>(null);
  const waveRef = useRef<any>(null);
 
  const normalizedSearch = searchText.trim().toLowerCase();
 
  useEffect(() => {
    if (!waveformRef.current) return;
 
    waveRef.current = WaveSurfer.create({
      container: waveformRef.current,
      waveColor: '#3b82f6',
      progressColor: '#38bdf8',
      height: 50,
      barWidth: 2,
      barGap: 2,
      backend: 'MediaElement',
    });
 
    return () => waveRef.current?.destroy();
  }, []);
 
  useEffect(() => {
    const handler = (e: any) => {
      const url = e.detail;
 
      if (!waveRef.current || !url) return;
 
      const ws = waveRef.current;
 
      ws.load(url);
 
      ws.once('ready', () => {
        ws.play();
      });
    };
 
    window.addEventListener('GLOBAL_AUDIO_PLAY', handler);
 
    return () => {
      window.removeEventListener('GLOBAL_AUDIO_PLAY', handler);
    };
  }, []);
 
  const filteredData = useMemo(() => {
    if (!normalizedSearch) return data;
 
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
      <div
        style={{
          background: '#0f172a',
          padding: 12,
          borderRadius: 10,
          marginBottom: 10,
        }}
      >
        <div style={{ display: 'flex', alignItems: 'center', gap: 10 }}>
          <button
            onClick={() => waveRef.current?.playPause()}
            style={{
              background: '#38bdf8',
              border: 'none',
              borderRadius: '50%',
              width: 36,
              height: 36,
              cursor: 'pointer',
            }}
          >
            ▶
          </button>
 
          <div style={{ flex: 1 }}>
            <div ref={waveformRef} />
          </div>
 
          <button
            onClick={() =>
              waveRef.current?.setPlaybackRate(
                waveRef.current.getPlaybackRate() === 1 ? 1.5 : 1,
              )
            }
            style={{
              background: '#1e293b',
              color: '#fff',
              border: 'none',
              padding: '6px 10px',
              borderRadius: 6,
              cursor: 'pointer',
            }}
          >
            1x / 1.5x
          </button>
        </div>
      </div>
 
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


/**
 * Licensed to the Apache Software Foundation (ASF) under one
 * or more contributor license agreements.  See the NOTICE file
 * distributed with this work for additional information
 * regarding copyright ownership.  The ASF licenses this file
 * to you under the Apache License, Version 2.0 (the
 * "License"); you may not use this file except in compliance
 * with the License.  You may obtain a copy of the License at
 *
 *   http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing,
 * software distributed under the License is distributed on an
 * "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 * KIND, either express or implied.  See the License for the
 * specific language governing permissions and limitations
 * under the License.
 */
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
          window.dispatchEvent(new CustomEvent('GLOBAL_AUDIO_PLAY', { detail: absoluteUrl }), );
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




