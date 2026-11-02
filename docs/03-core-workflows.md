# 3. Core Workflows

## Live camera-to-ASCII
1. `AsciiCanvas` requests camera access with an ideal 640×480 user-facing stream.
2. The stream is attached to a video element.
3. A requestAnimationFrame loop waits for current frame data.
4. The frame is mirrored into a hidden canvas and pixel data is read.
5. A fixed smoothing factor blends current pixels with the previous frame.
6. Brightness, contrast, and gain are applied; brightness maps to a character.
7. Characters are drawn to the visible canvas continuously.

If camera setup fails, an error message asks the user to allow permissions. On unmount, stream tracks are stopped and ambient hum is stopped.

## Change visual settings
The control panel updates shared settings. The rendering effect restarts when its options dependency changes. Modes: `matrix`, `bw`, `retro`, `color`. Density maps: `simple`, `complex`, `binary`, `blocks`.

## Export screenshot
The snapshot action calls `canvas.toDataURL('image/png')`, creates a temporary download anchor, and saves a timestamped `cyber_ascii_<timestamp>.png` file. It exports the rendered ASCII canvas, not the raw camera frame.

## AI analysis
1. The user selects Scan & Analyze.
2. The visible canvas is serialized as PNG and passed to the app capture callback.
3. The modal opens and loading state is enabled.
4. The Gemini service sends the image and prompt requesting JSON fields `description`, `threatLevel`, and `tags`.
5. Parsed results appear in the modal. Failures return an error-style result.
6. Loading state is cleared.

The threat-level field is AI-generated text and must not be treated as a real security determination. See [workflow sequence diagram](diagrams/workflow-sequence.mmd).
