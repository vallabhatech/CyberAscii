# 7. Limitations and Future Work

## Observed gaps

| Gap | Evidence / impact |
| --- | --- |
| Client-side API key injection | Vite defines Gemini key values in client bundle |
| Threat-level label not validated | Generated from prompt; no evaluation evidence |
| No test script | Package scripts list dev, build, preview only |
| No application database | No schema or migrations found |
| Resolution option appears unused | Present in types and initial state, not used by main renderer |
| External service dependency | AI analysis needs network, key, quota, and model availability |
| Browser permission dependency | Camera use needs user approval and supported browser |
| CDN assets | Tailwind and fonts reference external CDNs |

## Recommended future work

### High priority
1. Move Gemini calls server-side and protect credentials.
2. Add automated tests for brightness mapping, density maps, settings boundaries, and error handling.
3. Add privacy and consent information before external image processing.
4. Validate model responses at runtime and improve error feedback.

### Medium priority
5. Implement or remove the resolution setting.
6. Profile performance across viewport sizes and low-powered devices.
7. Improve accessibility for controls, keyboard operation, status announcements, and reduced motion.
8. Document the actual hosting provider and HTTPS deployment procedure.

### Lower priority
9. Add optional image-file input.
10. Let users mute or configure sound effects.
11. Document contribution and dependency update workflows.

## Verification status
No test suite was run and no test command is declared in the inspected package scripts. Build success, browser compatibility, frame rate, and AI accuracy remain unverified.
