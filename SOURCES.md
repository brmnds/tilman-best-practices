# Sources and adaptation

**Initial source review: 18 October 2026.**

This collection was adapted from local LuminaOS web and mobile engineering guidance and Tilman's shared AI co-working steering. It contains newly written public explanations and generic templates, rather than a mirror of those private repositories.

## Source families

| Source family | Guidance consulted | Public adaptation |
| --- | --- | --- |
| LuminaOS web agent entry point | Root `AGENTS.md` | Compact authority map, task boundaries, targeted reading, exact release evidence |
| Web engineering and development steering | Engineering principles; development standards | Simplicity, modularity, contracts, preservation of behavior, documentation ownership |
| Web verification and frontend steering | Testing; frontend performance | Risk tiers, evidence reuse, explicit caching, optimistic state and retry discipline |
| Web data steering | Database guidelines and database boundaries in the agent guide | Owner-scoped access, schema verification, controlled migrations, rollout records |
| Web AI feature steering | Coach principles; memory principles | Trusted identity, canonical transcripts, single writer ownership, idempotency, correlation |
| LuminaOS mobile agent entry point | Root `AGENTS.md` | Repository boundaries, mobile-owned UX, platform-specific validation and distribution states |
| Mobile architecture steering | Engineering principles; component architecture; web app research protocol | Platform-appropriate simplicity, focused lifecycle ownership, shared product contracts |
| Mobile state and reliability steering | Data fetching standards; data management; API reliability; mutation settlement | Owner-scoped caches, durable queues, offline reads, honest save states, background projection |
| Mobile interaction and verification steering | Keyboard handling; testing and validation | One keyboard owner, reachable controls, lifecycle QA, risk profiles and artifact evidence |
| Shared co-working and Skillbook guidance | Source-of-truth rules and repository conventions | Canonical reusable skills, source versus installed copies, maintained Markdown, explicit action boundaries |

## Adaptation rules

- Keep the reasoning and reusable practices; remove private access paths, account details, exact production topology, identifiers, and operational commands.
- Prefer current, explicit authority over older examples or broad rules. Source documents can contain historical sections; their existence does not make those sections current instructions.
- Preserve meaningful differences between web and mobile. Their original authority hierarchies and release paths are project-specific; the templates provide an adaptable structure.
- Keep provider-specific API calls, model names, version numbers, and performance heuristics out of universal rules. Verify those against current documentation when implementing.
- Describe practices as practices. Reviewing a source file does not certify deployed behavior, test coverage, privacy compliance, device acceptance, or store approval.

## Maintaining provenance

When adding material, record the source family, the practice adapted, the review date, and material changes in interpretation. Keep private source locations and review evidence in the maintainer's private workspace. Public readers should not need access to a private document to understand or use a guide.
