# archimate-studio

Web-based ArchiMate modeling tool built on top of [Archi](https://www.archimatetool.com/) Core, with MCP support for AI-assisted enterprise architecture.

> **Status:** Early development (spec phase)

## What is this?

A web-oriented ArchiMate editor that:

- Uses **Archi Core** (Java/EMF/OSGi) as the engine — no business logic rewrite
- Provides a **web UI** for visual ArchiMate diagram editing (React + JointJS)
- Supports **MCP protocol** for AI assistants (AI assistants)
- Stores models in **Git** (Grafico format) — compatible with desktop Archi + coArchi
- Enables **human + AI collaboration** on architecture models in real-time

## Architecture

```
  Browser              AI           Archi Desktop
    │                    │                      │
    │ REST + SSE         │ MCP (JSON-RPC)       │ coArchi (Git)
    ▼                    ▼                      ▼
┌─────────────────────────────────────────────────┐
│              archimate-studio server             │
│  REST API  ·  MCP Server  ·  Event Bus (SSE)    │
│                    │                             │
│            Archi Core (headless Equinox)         │
│            Grafico ←→ JGit                       │
└────────────────────┼─────────────────────────────┘
                     │ git push/pull
                     ▼
              Git Remote (GitHub, GitLab, ...)
```

## Tech Stack

**Backend:** Java 21+, Helidon SE 4.x, Eclipse Equinox (headless), JGit
**Frontend:** React, JointJS, Zustand, shadcn/ui, Tailwind CSS v4, Vite
**MCP:** helidon-mcp (Streamable HTTP + SSE + STDIO transports)

## Documentation

- [Project Specification](docs/archi-web-spec.wip.md) (WIP)

## Disclaimer

This project is **not affiliated with or endorsed by** the [Archi](https://www.archimatetool.com/) project or Phillip Beauvoir. "ArchiMate" is a registered trademark of [The Open Group](https://www.opengroup.org/).

This project uses Archi Core as a library. Archi source code is available at https://github.com/archimatetool/archi under the MIT License.

Eclipse Equinox and EMF source code is available at https://www.eclipse.org/ under the Eclipse Public License 2.0.

## License

Licensed under the [Apache License 2.0](LICENSE).

See [NOTICE](NOTICE) for third-party attribution.
