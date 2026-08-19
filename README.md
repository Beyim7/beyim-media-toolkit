# beyim-media-toolkit
# BEYIM

A free, local-first media toolkit that runs entirely in your browser. No uploads, no server, no accounts — your files never leave your device.

**[https://beyim7.github.io/beyim-media-toolkit/](#)** 

## Features

**Video**
- Convert video to MP3
- Compress video to a target file size (fast, single-pass)
- Trim video with a drag-to-select range slider

**Image**
- Compress images with a live size preview (KB/MB)
- Crop & resize with aspect ratio presets (1:1, 4:3, 16:9, 9:16, 3:2) or exact px / mm / cm dimensions
- Convert between PNG, JPEG, and WEBP

All processing happens on-device using [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) and the HTML5 Canvas API. Nothing is ever uploaded anywhere.

## Tech

- Vanilla HTML / CSS / JavaScript
- [Tailwind CSS](https://tailwindcss.com/) (CDN)
- [Lucide Icons](https://lucide.dev/)
- [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) (self-hosted in `/vendor`)

## Running locally

Because ffmpeg.wasm uses Web Workers, this needs to be served over `http(s)://`, not opened directly as a `file://` path.

1. Clone the repo
2. Serve the folder with any static server, e.g.:
   ```
   npx serve .
   ```
   or use the VS Code "Live Server" extension
3. Open the local address it gives you

## Why the `vendor` folder?

The ffmpeg.wasm library needs to spawn a Web Worker, and browsers block that if the worker script is loaded from a different origin (e.g. a CDN) than the page itself. The files in `/vendor` are the ffmpeg.wasm library, hosted locally, so everything runs same-origin.

## License

MIT
