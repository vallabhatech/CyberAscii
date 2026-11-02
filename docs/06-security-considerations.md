# 6. Security Considerations

## Camera privacy
The browser prompts for camera permission. Camera frames are processed in browser canvas elements. The component cleanup stops stream tracks on unmount. Users should be clearly informed when the camera is active and how to revoke permission.

## External image transfer
When the user requests AI analysis, the rendered canvas image is sent to Google Gemini through the SDK. Avoid capturing sensitive people, documents, screens, or surroundings without appropriate consent. The inspected repository does not include a privacy policy or detailed retention statement.

## API key exposure — high priority
`vite.config.ts` defines environment values into client code, and `geminiService.ts` reads `process.env.API_KEY`. Build-time frontend substitution is not a secret store: a key embedded in browser JavaScript can be extracted.

Recommended remediation: move requests to a server-side function, store the key in server-only environment variables, validate requests, apply rate limits, and never return credentials to the browser. This is not currently implemented in the inspected code.

## AI threat-level field
The service asks the model for a threat-level string. No calibrated classifier, security dataset evaluation, or validation process was found. Treat the output as an AI-generated description, not a real-world security verdict.

## Error handling
The service checks for a missing key and empty response, catches request/parse errors, and returns a structured error result. A custom backend validation layer and dedicated request-size limit were not found.

## Production checklist
- [ ] Keep Gemini key server-side.
- [ ] Add appropriate request validation and rate limits.
- [ ] Publish a privacy notice for camera use and external AI processing.
- [ ] Test permission-denied, offline, quota, and malformed-response cases.
- [ ] Make camera-active status accurate and visible.
- [ ] Avoid presenting generated threat labels as authoritative.
