import { ControlPanelConfig } from '@superset-ui/chart-controls';

const config: ControlPanelConfig = {
  controlPanelSections: [
    {
      label: 'Audio Settings',
      expanded: true,
      controlSetRows: [
        [
          {
            name: 'audio_url_column',
            config: {
              type: 'SelectControl',
              label: 'Audio URL Column',
              default: 'audio_url',
              clearable: false,
              renderTrigger: false,
              mapStateToProps: ({ datasource }) => ({
                choices:
                  datasource?.columns?.map((col: any) => [
                    col.column_name,
                    col.column_name,
                  ]) || [],
              }),
            },
          },
        ],
        [
          {
            name: 'label_column',
            config: {
              type: 'SelectControl',
              label: 'Label Column',
              default: 'audio_name',
              clearable: false,
              renderTrigger: false,
              mapStateToProps: ({ datasource }) => ({
                choices:
                  datasource?.columns?.map((col: any) => [
                    col.column_name,
                    col.column_name,
                  ]) || [],
              }),
            },
          },
        ],
        [
          {
            name: 'gradient_start',
            config: {
              type: 'ColorPickerControl',
              label: 'Gradient Start',
              default: '#6366F1',
              renderTrigger: true,
            },
          },
          {
            name: 'gradient_end',
            config: {
              type: 'ColorPickerControl',
              label: 'Gradient End',
              default: '#8B5CF6',
              renderTrigger: true,
            },
          },
        ],
        [
          {
            name: 'row_limit',
            config: {
              type: 'TextControl',
              label: 'Number of Audios',
              default: 5,
              renderTrigger: false,
            },
          },
        ],
      ],
    },
  ],
};

export default config;




import React, { useRef, useState } from 'react';

function formatTime(seconds: number) {
  if (!seconds || isNaN(seconds)) return '00:00';

  const mins = Math.floor(seconds / 60);
  const secs = Math.floor(seconds % 60);

  return `${String(mins).padStart(2, '0')}:${String(secs).padStart(
    2,
    '0',
  )}`;
}

function AudioPlayer({
  src,
  gradientStart,
  gradientEnd,
}: {
  src: string;
  gradientStart: string;
  gradientEnd: string;
}) {
  const audioRef = useRef<HTMLAudioElement>(null);
  const barRef = useRef<HTMLDivElement>(null);

  const [playing, setPlaying] = useState(false);
  const [progress, setProgress] = useState(0);
  const [duration, setDuration] = useState(0);
  const [current, setCurrent] = useState(0);

  const togglePlay = () => {
    if (!audioRef.current) return;

    if (playing) {
      audioRef.current.pause();
    } else {
      audioRef.current.play();
    }

    setPlaying(!playing);
  };

  const skip = (seconds: number) => {
    if (!audioRef.current) return;

    audioRef.current.currentTime = Math.min(
      Math.max(audioRef.current.currentTime + seconds, 0),
      audioRef.current.duration || 0,
    );
  };

  const onTimeUpdate = () => {
    if (!audioRef.current) return;

    const currentTime = audioRef.current.currentTime;
    const total = audioRef.current.duration || 0;

    setCurrent(currentTime);
    setDuration(total);
    setProgress((currentTime / total) * 100 || 0);
  };

  const seekAudio = (e: React.MouseEvent<HTMLDivElement>) => {
    if (!barRef.current || !audioRef.current) return;

    const rect = barRef.current.getBoundingClientRect();
    const clickX = e.clientX - rect.left;

    const percent = (clickX / rect.width) * 100;

    audioRef.current.currentTime =
      (percent / 100) * audioRef.current.duration;

    setProgress(percent);
  };

  const controlBtnStyle = {
    width: 42,
    height: 42,
    minWidth: 42,
    borderRadius: '50%',
    border: 'none',
    background: '#0F172A',
    color: '#fff',
    cursor: 'pointer',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    fontSize: 14,
    fontWeight: 600,
    flexShrink: 0,
  };

  return (
    <div
      style={{
        display: 'flex',
        alignItems: 'center',
        gap: 14,
        width: '100%',
      }}
    >
      {/* BACK 5 SEC */}
      <button
        onClick={() => skip(-5)}
        style={controlBtnStyle}
      >
       {'<'}
      </button>

      {/* PLAY BUTTON */}
      <button
        onClick={togglePlay}
        style={{
          ...controlBtnStyle,
          width: 48,
          height: 48,
          minWidth: 48,
          fontSize: 18,
          paddingLeft: playing ? 0 : 3,
        }}
      >
        {playing ? '❚❚' : '▶'}
      </button>

      {/* FORWARD 5 SEC */}
      <button
        onClick={() => skip(5)}
        style={controlBtnStyle}
      >
        {'>'}
      </button>

      {/* PROGRESS BAR */}
      <div
        ref={barRef}
        onClick={seekAudio}
        style={{
          flex: 1,
          height: 8,
          borderRadius: 999,
          background: '#E5E7EB',
          position: 'relative',
          cursor: 'pointer',
        }}
      >
        <div
          style={{
            width: `${progress}%`,
            height: '100%',
            borderRadius: 999,
            background: `linear-gradient(90deg, ${gradientStart}, ${gradientEnd})`,
          }}
        />

        <div
          style={{
            position: 'absolute',
            top: '50%',
            left: `${progress}%`,
            transform: 'translate(-50%, -50%)',
            width: 16,
            height: 16,
            borderRadius: '50%',
            background: gradientEnd,
            border: '3px solid white',
            boxShadow: '0 2px 8px rgba(0,0,0,0.15)',
          }}
        />
      </div>

      {/* TIMESTAMP */}
      <div
        style={{
          minWidth: 100,
          textAlign: 'right',
          fontSize: 13,
          fontWeight: 500,
          color: '#94A3B8',
          display: 'flex',
          alignItems: 'center',
          justifyContent: 'center',
        }}
      >
        {formatTime(current)} / {formatTime(duration)}
      </div>

      <audio
        ref={audioRef}
        src={src}
        preload="metadata"
        onTimeUpdate={onTimeUpdate}
        onLoadedMetadata={() => {
          if (audioRef.current) {
            setDuration(audioRef.current.duration);
          }
        }}
        onEnded={() => setPlaying(false)}
      />
    </div>
  );
}

export default function AudioPlayerChart(props: any) {
  const data = props?.data || [];
  const formData = props?.formData || {};

  const audioCol = formData.audio_url_column || 'audio_url';

  const gradientStart =
    formData.gradient_start || '#6366F1';

  const gradientEnd =
    formData.gradient_end || '#8B5CF6';

  if (!data.length) {
    return <div>No audio data found</div>;
  }

  return (
    <div style={{ padding: 20 }}>
      {data.map((row: any, index: number) => {
        const rawUrl = row[audioCol];

        const audioUrl =
          rawUrl?.startsWith('http')
            ? rawUrl
            : `${window.location.origin}${rawUrl}`;

        return (
          <div
            key={index}
            style={{
              padding: 20,
              borderRadius: 14,
              background: 'rgba(0,0,0,0.88)',
              border: '1px solid rgb(226,232,240)',
            }}
          >
            <AudioPlayer
              src={audioUrl}
              gradientStart={gradientStart}
              gradientEnd={gradientEnd}
            />
          </div>
        );
      })}
    </div>
  );
}


import {
  buildQueryContext,
  QueryFormData,
} from '@superset-ui/core';

export default function buildQuery(formData: QueryFormData) {
  const customFormData = formData as QueryFormData & {
    audio_url_column?: string;
    label_column?: string;
    row_limit?: number;
  };

  return buildQueryContext(formData, baseQueryObject => [
    {
      ...baseQueryObject,

      columns: [
        customFormData.label_column || 'audio_name',
        customFormData.audio_url_column || 'audio_url',
      ],

      metrics: [],

      row_limit: Number(customFormData.row_limit) || 5,
    },
  ]);
}


import {
  ChartMetadata,
  ChartPlugin,
} from '@superset-ui/core';

import buildQuery from './buildQuery';
import controlPanel from './config/controlPanel';
import transformProps from './transformProps';

export default class AudioPlayerChartPlugin extends ChartPlugin {
  constructor() {
    super({
      loadChart: () => import('./AudioPlayerChart'),
      metadata: new ChartMetadata({
        name: 'Audio Player Chart',
        description: 'Custom Audio Player Chart',
        thumbnail: '',
      }),
      transformProps,
      buildQuery,
      controlPanel,
    });
  }
}




import { ChartProps } from '@superset-ui/core';

export default function transformProps(chartProps: ChartProps) {
  const payload = chartProps.queriesData?.[0] || {};

  return {
    data: payload.data || [],
    formData: chartProps.formData || {},
    width: chartProps.width,
    height: chartProps.height,
  };
}



import { QueryFormData } from '@superset-ui/core';

export interface AudioPlayerFormData extends QueryFormData {
  audio_url_column: string;
  label_column: string;
  row_limit: number;
}





