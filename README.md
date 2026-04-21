s3://bucket-cx-insightshub-dev/audio_files/

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
    background: '#c5d0e9',
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
          background: '#b5c8ec',
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
          color: '#050606',
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
    formData.gradient_start || '#7375e9';
 
  const gradientEnd =
    formData.gradient_end || '#b19ae6';
 
  if (!data.length) {
    return <div>No audio data found</div>;
  }
 
  return (
    <div style={{ padding: 20 }}>
      {data.map((row: any, index: number) => {
        const rawUrl = row[audioCol];
        const DEFAULT_AUDIO_BASE_PATH = '/static/assets/common-audio/';
 
         const audioUrl =
          rawUrl?.startsWith('http://') ||
          rawUrl?.startsWith('https://')
      ? rawUrl
      : rawUrl?.startsWith('/static/')
      ? `${window.location.origin}${rawUrl}`
      : `${window.location.origin}${DEFAULT_AUDIO_BASE_PATH}${rawUrl}`;
 
        return (
          <div
            key={index}
            style={{
              padding: 20,
              borderRadius: 14,
              background: 'rgba(90, 117, 240, 0.99)',
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
 
