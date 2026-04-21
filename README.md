CREATE TABLE audio_files (
    id SERIAL PRIMARY KEY,
    audio_url TEXT
);

INSERT INTO audio_files (audio_url) VALUES
('https://bucket-cx-insightshub-dev.s3.us-east-1.amazonaws.com/audio_files/heartify-flute-music-363036.mp3'),
('https://bucket-cx-insightshub-dev.s3.us-east-1.amazonaws.com/audio_files/ortensialily-mythical-tune-276246.mp3'),
('https://bucket-cx-insightshub-dev.s3.us-east-1.amazonaws.com/audio_files/saseendran-rain-tune-indain-raga-354626.mp3');
