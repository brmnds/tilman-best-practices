# Web app development

Build understandable systems, preserve working behavior, and make completion verifiable. These guides adapt LuminaOS web/backend practices to projects that use coding agents alongside human engineers.

## Reading map

| Guide | Use it when |
| --- | --- |
| [Engineering principles](engineering-principles.md) | Choosing the default way to build and review |
| [Agent context and steering](agent-context-and-steering.md) | Structuring `AGENTS.md`, specifications, runbooks, and reusable skills |
| [Architecture and contracts](architecture-and-contracts.md) | Defining modules, service boundaries, and typed interfaces |
| [Frontend quality](frontend-quality.md) | Improving responsiveness, cache behavior, accessibility, and feedback |
| [Data and migrations](data-and-migrations.md) | Changing stored data, authorization, or schemas |
| [AI feature reliability](ai-feature-reliability.md) | Building an AI feature with tools, memory, and recoverable writes |
| [Testing and release](testing-and-release.md) | Selecting checks and recording what actually shipped |

## Copy and adapt

- [AGENTS.md template](templates/AGENTS.md)
- [Change brief](templates/change-brief.md)
- [Release evidence](templates/release-evidence.md)

Example: for an agent fixing a login bug, start with the change brief, route it to authentication steering and the current contract, cover recovery and denial cases, then record local and deployed results separately. A successful login is only one part of the acceptance evidence.

For shared mobile behavior, also read [mobile feature parity](../Mobile%20development/templates/feature-parity.md).
