# 2. System Architecture

## Architecture
The application is a client-side React SPA. Camera capture, frame processing, rendering controls, and screenshot export run in the browser. AI analysis is an external Google Gemini SDK call. No custom backend or database was found in the inspected files.

| Module | Responsibility |
| --- | --- |
| `index.tsx` | Mount React application |
| `App.tsx` | Own settings and analysis/modal state |
| `AsciiCanvas.tsx` | Camera lifecycle, animation loop, rendering, capture/export |
| `ControlPanel.tsx` | Change visual settings |
| `AnalysisModal.tsx` | Show loading and analysis results |
| `asciiConverter.ts` | Map brightness to selected characters |
| `geminiService.ts` | Call Gemini and parse JSON |
| `soundEffects.ts` | Generate audio with Web Audio |
| `types.ts` | Shared settings, result types, density maps |
| Vite | Development server, build, and environment definitions |

## Rendering pipeline
1. Request a user-facing camera stream.
2. Draw a horizontally mirrored video frame to a hidden canvas.
3. Read RGBA pixel data and blend it with the previous frame using fixed temporal smoothing.
4. Calculate weighted brightness, apply contrast and gain, and clamp values.
5. Map brightness to a character in the selected density map.
6. Draw characters to the visible canvas using the selected color mode.

The renderer's columns and rows are derived from visible canvas size and font size. The `resolution` option exists in the type and initial state but is not used by the inspected main rendering loop.

## AI pipeline
The visible ASCII canvas is serialized as a PNG data URL. `analyzeImage` strips the data URL prefix and sends the image plus a JSON-output prompt through the Google Gen AI SDK. The configured model string is `gemini-3-flash-preview`. The expected fields are `description`, `threatLevel`, and `tags`.

## Diagram
See [system architecture](diagrams/system-architecture.mmd).

## Persistence and APIs
No app database, migrations, custom API routes, or backend service were found in inspected files. Screenshot export downloads a file; analysis results are kept in UI state.
