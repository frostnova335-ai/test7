import React, { useRef, useState } from 'react';

function formatTime(seconds: number) {
  if (!seconds || isNaN(seconds)) return '00:00';

  const mins = Math.floor(seconds / 60);
  const secs = Math.floor(seconds % 60);

  return `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
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
  const audioRef = useRef<HTMLVideoElement>(null); // using VIDEO for stability
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
      audioRef.current.play().catch(err => {
        console.error('Play failed:', err);
      });
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
  };

  return (
    <div style={{ display: 'flex', alignItems: 'center', gap: 14, width: '100%' }}>

      <button onClick={() => skip(-5)} style={controlBtnStyle}>{'<'}</button>

      <button
        onClick={togglePlay}
        style={{ ...controlBtnStyle, width: 48, height: 48, fontSize: 18 }}
      >
        {playing ? '❚❚' : '▶'}
      </button>

      <button onClick={() => skip(5)} style={controlBtnStyle}>{'>'}</button>

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
      </div>

      <div style={{ minWidth: 100, textAlign: 'right', fontSize: 13 }}>
        {formatTime(current)} / {formatTime(duration)}
      </div>

      {/* 🔥 KEY FIX: using VIDEO instead of AUDIO */}
      <video
        ref={audioRef}
        src={src}
        style={{ display: 'none' }}
        preload="metadata"
        crossOrigin="anonymous"
        onTimeUpdate={onTimeUpdate}
        onLoadedMetadata={() => {
          if (audioRef.current) {
            setDuration(audioRef.current.duration);
          }
        }}
        onEnded={() => setPlaying(false)}
        onError={(e) => {
          console.error('Audio error:', src, e);
        }}
      />
    </div>
  );
}

export default function AudioPlayerChart(props: any) {
  const data = props?.data || [];
  const formData = props?.formData || {};

  const audioCol = formData.audio_url_column || 'audio_url';
  const gradientStart = formData.gradient_start || '#6366F1';
  const gradientEnd = formData.gradient_end || '#8B5CF6';

  if (!data.length) {
    return <div>No audio data found</div>;
  }

  return (
    <div style={{ padding: 20 }}>
      {data.map((row: any, index: number) => {
        const rawUrl = row[audioCol];

        if (!rawUrl) {
          console.error("Missing audio URL in row:", row);
          return null;
        }

        const audioUrl =
          typeof rawUrl === 'string' && rawUrl.startsWith('http')
            ? rawUrl
            : typeof rawUrl === 'string' && rawUrl.startsWith('/static/')
              ? `${window.location.origin}${rawUrl}`
              : rawUrl;

        console.log("ROW DATA:", row);
        console.log("AUDIO COLUMN:", audioCol);
        console.log("RAW URL:", rawUrl);
        console.log("FINAL URL:", audioUrl);

        console.log("PLAYING URL:", audioUrl);

        return (
          <div
            key={index}
            style={{
              padding: 20,
              borderRadius: 14,
              background: '#6366F1',
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
