# CyberAscii Documentation

This documentation is based on the source files inspected on the repository's main branch. Unverified behavior is called out rather than assumed.

## Documents
1. [Project overview](01-project-overview.md)
2. [System architecture](02-system-architecture.md)
3. [Core workflows](03-core-workflows.md)
4. [Installation and configuration](04-setup-and-configuration.md)
5. [Security considerations](06-security-considerations.md)
6. [Limitations and future work](07-limitations-and-future-work.md)
7. [Glossary and references](08-glossary-and-references.md)

## Diagrams
- [System architecture](diagrams/system-architecture.mmd)
- [Workflow sequence](diagrams/workflow-sequence.mmd)
- [Application data flow](diagrams/data-flow.mmd)

## Evidence reviewed
`App.tsx`, `index.tsx`, `components/AsciiCanvas.tsx`, `components/ControlPanel.tsx`, `components/AnalysisModal.tsx`, `services/geminiService.ts`, `utils/asciiConverter.ts`, `utils/soundEffects.ts`, `types.ts`, `package.json`, and `vite.config.ts`.

No test script, custom backend routes, application database, or migrations were found in the files inspected. Runtime behavior and build success were not tested through the connector.
