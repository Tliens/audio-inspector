# Audio Inspector

Free online audio debugging tools for developers — 100% client-side, nothing ever uploaded.

**Live: https://tliens.github.io/audio-inspector/**

## Features

- **Format analysis** — container/codec detection via magic bytes (extensions can lie), duration, sample rate, channels, bit depth, bitrate (header or computed)
- **Header inspection** — hand-written parsers for WAV/RIFF, AIFF/AIFC, MP3 (ID3v1/v2, MPEG frames, Xing/LAME), FLAC, Ogg (Vorbis/Opus/embedded FLAC), MP4/M4A (AAC esds, ALAC, Opus, FLAC), Matroska/WebM, ADTS AAC, AMR, WMA/ASF, Sun AU, CAF — with a linked hex viewer (click a structure node → bytes highlighted)
- **Waveform & spectrum** — zoomable waveform with selection stats, offline spectrogram (FFT 1024), live spectrum during playback
- **Level statistics** — peak, RMS, crest factor, DC offset, clipping detection
- **Demo files** — 21 CC0 samples in 10+ formats (speech, 20 Hz–20 kHz sweep, chord comparisons, edge cases like a clipped WAV, DC offset, and an MP3 wearing a .wav name)
- **Compression** — MP3 (CBR/VBR), AAC/M4A, Ogg Vorbis, Opus, WebM, FLAC, WAV; bitrate/sample-rate/channel/loudnorm options; batch queue; A/B playback; equivalent ffmpeg command shown; powered by ffmpeg.wasm (core loaded on demand from CDN, runs locally)

## Tech

Single-file site (`index.html`, vanilla JS, no build step) + vendored `ffmpeg/` wrapper (MIT, from @ffmpeg/ffmpeg 0.12.15). The ffmpeg.wasm core (~31 MB) is fetched on first compression from jsDelivr (with mirror fallback) and cached by the browser. English/中文 UI, dark/light themes, `?lang=` deep links.

## Run locally

```bash
python3 -m http.server 8799
# open http://localhost:8799/
```

## License

Site code: MIT. Demo audio: CC0 (synthesized locally with ffmpeg + macOS TTS).
