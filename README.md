/**
 * Licensed to the Apache Software Foundation (ASF) under one
 * or more contributor license agreements.  See the NOTICE file
 * distributed with this work for additional information
 * regarding copyright ownership.  The ASF licenses this file
 * to you under the Apache License, Version 2.0 (the
 * "License"); you may use this file except in compliance
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
