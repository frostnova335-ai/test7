import React, { useRef, useState, useEffect } from 'react';

function formatTime(seconds: number) {
  if (!seconds || isNaN(seconds)) return '00:00';

  const mins = Math.floor(seconds / 60);
  const secs = Math.floor(seconds % 60);

  return `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
}

function AudioPlayer({ src, color }: { src: string; color: string }) {
  const audioRef = useRef<HTMLVideoElement>(null);
  const barRef = useRef<HTMLDivElement>(null);

  const [playing, setPlaying] = useState(false);
  const [progress, setProgress] = useState(0);
  const [duration, setDuration] = useState(0);
  const [current, setCurrent] = useState(0);

  // 🔥 DEBUG: check URL accessibility
  useEffect(() => {
    if (!src) return;

    console.log('🔗 AUDIO URL:', src);

    fetch(src, { method: 'HEAD' })
      .then(res => {
        console.log('✅ FETCH SUCCESS:', res.status);
        console.log('📦 HEADERS:', {
          contentType: res.headers.get('content-type'),
          contentLength: res.headers.get('content-length'),
        });
      })
      .catch(err => {
        console.error('❌ FETCH FAILED (CORS or access issue):', err);
      });
  }, [src]);

  // 🔥 attach all audio debug events
  useEffect(() => {
    const audio = audioRef.current;
    if (!audio) return;

    const events = [
      'loadstart',
      'loadedmetadata',
      'loadeddata',
      'canplay',
      'canplaythrough',
      'play',
      'pause',
      'ended',
      'error',
      'stalled',
      'waiting',
    ];

    events.forEach(event => {
      audio.addEventListener(event, () => {
        console.log(`🎧 AUDIO EVENT: ${event}`, {
          currentTime: audio.currentTime,
          duration: audio.duration,
          readyState: audio.readyState,
        });
      });
    });

    return () => {
      events.forEach(event => audio.removeEventListener(event, () => { }));
    };
  }, []);

  const togglePlay = async () => {
    if (!audioRef.current) return;

    console.log('▶️ TOGGLE PLAY');

    try {
      if (playing) {
        audioRef.current.pause();
      } else {
        await audioRef.current.play();
      }
      setPlaying(!playing);
    } catch (err) {
      console.error('❌ PLAY FAILED:', err);
    }
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
    background: '#000',
    color: '#fff',
    cursor: 'pointer',
  };

  // 🔥 Important trick for mp4 streaming
  const fixedUrl = src ? src + '#t=0.1' : '';

  return (
    <div style={{ display: 'flex', alignItems: 'center', gap: 14 }}>

      <button onClick={() => skip(-5)} style={controlBtnStyle}>
        {'<'}
      </button>

      <button onClick={togglePlay} style={{ ...controlBtnStyle, width: 48, height: 48 }}>
        {playing ? '❚❚' : '▶'}
      </button>

      <button onClick={() => skip(5)} style={controlBtnStyle}>
        {'>'}
      </button>

      {/* progress bar */}
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
            background: color,
          }}
        />

        <div
          style={{
            position: 'absolute',
            top: '50%',
            left: `${progress}%`,
            transform: 'translate(-50%, -50%)',
            width: 14,
            height: 14,
            borderRadius: '50%',
            background: color,
            border: '2px solid white',
          }}
        />
      </div>

      <div style={{ minWidth: 100, fontSize: 12 }}>
        {formatTime(current)} / {formatTime(duration)}
      </div>

      {/* 🔥 FINAL AUDIO TAG (FIXED) */}
      <video
        ref={audioRef}
        preload="metadata"
        crossOrigin="anonymous"
        style={{ display: 'none' }}
        onLoadStart={() => console.log('🚀 LOAD START:', src)}
        onLoadedMetadata={() => {
          console.log('✅ METADATA LOADED:', audioRef.current?.duration);
          if (audioRef.current) {
            setDuration(audioRef.current.duration);
          }
        }}
        onCanPlay={() => console.log('🎧 CAN PLAY')}
        onCanPlayThrough={() => console.log('🎧 CAN PLAY THROUGH')}
        onError={(e) => {
          console.error('❌ VIDEO ERROR:', src);
          console.error('ERROR EVENT:', e);
          console.error('NETWORK STATE:', audioRef.current?.networkState);
          console.error('READY STATE:', audioRef.current?.readyState);
        }}
      >
        <source src={src} type="video/mp4" />
      </video>
    </div>
  );
}

export default function AudioPlayerChart(props: any) {
  const data = props?.data || [];
  const formData = props?.formData || {};

  const audioCol = formData.audio_url_column || 'signed_url';
  const color = formData.color_picker || '#E0F2FE';

  console.log('📊 DATA RECEIVED:', data);

  if (!data.length) {
    return <div>No audio data found</div>;
  }

  return (
    <div style={{ padding: 20 }}>
      {data.map((row: any, index: number) => {
        const rawUrl = row[audioCol];
        const audioUrl = rawUrl?.trim();

        console.log(`🎵 ROW ${index} URL:`, audioUrl);

        return (
          <div
            key={index}
            style={{
              padding: 20,
              borderRadius: 14,
              background: '#f8fafc',
              marginBottom: 10,
            }}
          >
            <AudioPlayer src={audioUrl} color={color} />
          </div>
        );
      })}
    </div>
  );
}
