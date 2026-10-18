# Mobile development

Preserve shared product behavior while building an experience that fits iOS and Android. These practices come from a bare React Native project with native app targets, shared backend contracts, and offline-capable domains.

## Reading map

| Guide | Use it when |
| --- | --- |
| [Engineering principles](engineering-principles.md) | Setting architectural and dependency defaults |
| [Agent context and steering](agent-context-and-steering.md) | Defining mobile repository authority and task routing |
| [Architecture and state](architecture-and-state.md) | Separating screens, controllers, server state, and durable data |
| [Offline and sync](offline-and-sync.md) | Designing truthful saves, retry, replay, and reconnect |
| [Native UX and dependencies](native-ux-and-dependencies.md) | Choosing interaction primitives and checking platform cost |
| [Security and private media](security-and-private-media.md) | Handling account switches, tokens, downloads, and cleanup |
| [Testing and release](testing-and-release.md) | Selecting runtime checks and verifying distribution stages |

## Copy and adapt

- [AGENTS.md template](templates/AGENTS.md)
- [Cross-platform feature brief](templates/feature-parity.md)
- [Device QA record](templates/device-qa.md)
- [Release evidence](templates/release-evidence.md)

Start with [offline and sync](offline-and-sync.md) if you want one concrete reliability practice: the UI can settle after a server acknowledgment or a verified durable queue admission, while keeping later local projection work observable and recoverable.

The source app uses the React Native CLI. Follow your own project's chosen toolchain; installing a library with an Expo name does not establish that the application uses an Expo launch workflow.
