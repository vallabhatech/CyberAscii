# 4. Installation and Configuration

## Prerequisites
- Git, Node.js, and npm.
- Modern browser with Canvas 2D, MediaDevices, and Web Audio support.
- Camera permission for live rendering.
- Gemini API key for AI analysis.

No Node version is declared in the inspected package metadata.

## Install and run
```bash
git clone https://github.com/vallabhatech/CyberAscii.git
cd CyberAscii
npm install
npm run dev
```

Vite config specifies port `3000` and host `0.0.0.0`. Use the URL printed by Vite. Camera access generally requires a secure context; localhost is usually allowed.

## Gemini environment
Vite loads environment values and defines `process.env.API_KEY` and `process.env.GEMINI_API_KEY` from `GEMINI_API_KEY`. The service reads `process.env.API_KEY`.

Create a local `.env` file:
```dotenv
GEMINI_API_KEY=replace_with_your_key
```

Restart the dev server after changes. Never commit the actual key. **The current frontend build-time injection can expose the key to users.** For production, move calls to a server-side function and keep the key server-only.

| Variable | Required? | Purpose |
| --- | --- | --- |
| `GEMINI_API_KEY` | Only for AI analysis | Vite input used for the SDK key definition |

## Scripts
| Script | Command | Purpose |
| --- | --- | --- |
| dev | `npm run dev` | Development server |
| build | `npm run build` | Production bundle |
| preview | `npm run preview` | Preview production bundle |

No test or lint script is defined in inspected `package.json`. Commands are documented from configuration; they were not executed in this pass.

## Troubleshooting
- Camera denied: grant site permission and reload.
- Camera unavailable: check OS/browser permission and other apps using it.
- AI fails: verify key, network, quota, and provider model access.
- No audio: browser autoplay policy may require a user gesture.
- Port occupied: stop the conflicting process or intentionally change Vite config.
