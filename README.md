https://bucket-cx-insightshub-engine-deployment.s3.amazonaws.com/audio_files/2025-07-29-12-15-20_679169198508_VOICE_9ce980a5-7a07-4fbb-99f7-e292b18e83f7.mp4?AWSAccessKeyId=ASIA3TD2SHTXMM3YHY5P&Signature=bekQKA9z0nMX5PWlpVw5ls56vK8%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEIL%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJHMEUCIQDa72msreYes%2FfGxHEZBFWSEL%2B5Q0Rff2TgUu7qPEaOBwIgHwBLN8bVd3icQ4J%2FdW5x0EFQmN1WDu2jD482yKFeaXkqugUISxAAGgw3OTY5NzM0ODExOTgiDGrh3GCZMo9Tag6SNSqXBWUh8WAYhktZ8lFE9bjILcbpAJoSaF6ZIsd7aFTaYodFNX7enxftOyVefeY0OxpFvgIJTKNroVuGGZqy1s%2FyUzb052D1nNYwFrPpt7OW%2B6enKE5iv5lauYqXpNESXYNJqFsuXtrOvRMYdEQ1Kaei6G32GNzVLhccJ3olDW%2FMCD2b1yGSvzCR%2BlIvu%2FZypBkWeo6jn8IuPQ%2FyyzZGezJ2wyUn%2FBkFja4uI8e9167KnaiN2yRk2fWlWqp3CK1PMH1KbfO1gSzM%2F8z4Hbgn2IisbrY49UNDJtcr5K22H%2BF791DcGvnJfaDowLru0dT1mgC02C2FlNhNteFugan7prtDBPwgFPyjAYek%2F3y5jVbJLSNiOEGHQEJIHZF7wZlcTR6pLyO%2Ft4q9F5u%2BHWEvCBskWVW5y8M8nq6iE8u6%2B4c8rOPUVm%2BZ47GyX7dO8zseUmcD924l0IlyUb1yyhW9FVvQISHABHIKMQY1S89VZTJqm5cKJcRaEehOY3xBWkZrDEnctuO0tQKN5KG70atXg7zC4qD%2BVn9jzYYgCjD5%2FkZdpMXx7jV%2Fdum6d2u8OV3foHWa6qclCulN9aTyKNlixHn%2FJU88ZzL5o3BM0d9NFNXv4%2BC3t3cfMWpO0QowNrkhFEm7X2iqUFVNIxZZGGf9IGhEhKDXWpqeJRCLvjqyEdGuMBRqR2m3tvx%2FtzlJKG8m%2FBgB2wTonzR6346DeG8fEQyP1nm2C%2FGSbQNn5WfHCR1CDoFKZPcn6L%2BrQPCaKp6zGzjRkicNmt3Si2xBc4dtpHG5uYcEZurZIku%2BI%2Bx4JBTyMqwjVv9w2%2F%2FgBohrQMXV69oFrmAGAeZqfIBWv%2Bf70KLuQb1JtAYPA1QwtByO1Yd1TVUo%2B%2FIr8jhGgzC4uKLPBjqxAbZtlz8BZo1ahdtp%2BuKUlTkS5%2B6wJ%2BFva80Ay5IRa1LbREl0lh5%2BST64eWxLsD2VZL4kjYFuS12AEh94%2FlF7WsAFrf4%2BRPu3DAgHOQi17TiJ7IbGSKdmv07jqA4znCJuZmLEMzNgGW14ZHLDpEvaVcQC5LVhgXn6YxEOMy3tb9fFs1mF5Fo4j21Ls56mPtHmEdaVJBXTURIxU6VFHpbwf2NBsYWiGhqqx5iRIBx2ErPEIg%3D%3D&Expires=1776896020


import React, { useRef, useState } from 'react';

function formatTime(seconds: number) {
  if (!seconds || isNaN(seconds)) return '00:00';

  const mins = Math.floor(seconds / 60);
  const secs = Math.floor(seconds % 60);

  return `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
}

function AudioPlayer({
  src,
  color,
}: {
  src: string;
  color: string;
}) {
  const audioRef = useRef<HTMLAudioElement>(null);
  const barRef = useRef<HTMLDivElement>(null);

  const [playing, setPlaying] = useState(false);
  const [progress, setProgress] = useState(0);
  const [duration, setDuration] = useState(0);
  const [current, setCurrent] = useState(0);
  const togglePlay = async () => {
    if (!audioRef.current) return;

    try {
      if (playing) {
        audioRef.current.pause();
      } else {
        await audioRef.current.play();
      }
      setPlaying(!playing);
    } catch (err) {
      console.error('Play failed:', err);
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

      <audio
        ref={audioRef}
        preload="metadata"
        crossOrigin="anonymous"
        onTimeUpdate={onTimeUpdate}
        onLoadedMetadata={() => {
          if (audioRef.current) {
            setDuration(audioRef.current.duration);
          }
        }}
        onEnded={() => setPlaying(false)}
        onError={(e) => console.error('AUDIO ERROR:', src, e)}
      >
        <source src={src} type="audio/mp4" />
        <source src={src} type="video/mp4" />
      </audio>
    </div>
  );
}

export default function AudioPlayerChart(props: any) {
  const data = props?.data || [];
  const formData = props?.formData || {};

  const audioCol = formData.audio_url_column || 'url';
  const color = formData.color_picker || '#E0F2FE';

  if (!data.length) {
    return <div>No audio data found</div>;
  }

  return (
    <div style={{ padding: 20 }}>
      {data.map((row: any, index: number) => {
        const rawUrl = row[audioCol];
        const audioUrl = rawUrl?.trim();

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
