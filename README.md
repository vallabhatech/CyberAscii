# CyberAscii Vision

CyberAscii Vision is a browser-based cyberpunk-styled camera app that renders a live camera feed as ASCII art and can request AI-generated scene analysis.

## Features
- Live camera-to-ASCII rendering using browser MediaDevices and Canvas APIs.
- Matrix green, monochrome, amber retro, and full-color modes.
- Adjustable font size, brightness, contrast, and character density.
- PNG screenshot export.
- Optional Google Gemini analysis returning a description, tags, and a threat-level label.
- Synthesized interface sounds and ambient audio.

**Security note:** The current Vite configuration injects the Gemini API key into client-side code. Do not deploy a privileged key in a public client build; move AI requests behind a server-side proxy.

## Run locally
```bash
git clone https://github.com/vallabhatech/CyberAscii.git
cd CyberAscii
npm install
```

Create a root `.env` file if AI analysis is needed:
```dotenv
GEMINI_API_KEY=your_key_here
```

Then run:
```bash
npm run dev
```

Vite is configured for port `3000` and host `0.0.0.0`. Build and preview with `npm run build` and `npm run preview`.

## Project structure
- `App.tsx` — application state and top-level UI
- `components/AsciiCanvas.tsx` — camera, frame rendering, capture/export
- `components/ControlPanel.tsx` — visual controls
- `components/AnalysisModal.tsx` — AI result display
- `services/geminiService.ts` — Google Gen AI integration
- `utils/asciiConverter.ts` — brightness-to-character helpers
- `utils/soundEffects.ts` — Web Audio effects
- `types.ts` — shared types and character maps
- `vite.config.ts` — Vite configuration
- `docs/` — project documentation

See [the documentation index](docs/README.md). No automated test script is declared in `package.json`, and a build was not executed during documentation generation. The AI threat-level label is not a verified security assessment.
