# Tilman Best Practices

Practical engineering and AI coding workflows by **Tilman Resch**, adapted from building LuminaOS across web, iOS, and Android.

This is a growing collection of the principles, agent instructions, steering structures, and verification habits I use in my own projects. It is for people who want to make AI-assisted development more dependable and easier to maintain.

**Start with one practice, adapt it to your project, and make the result verifiable.**

## Choose your starting point

| Folder | What you will find | Start here |
| --- | --- | --- |
| [Web app development](Web%20app%20development/README.md) | Architecture, API contracts, frontend quality, migrations, AI feature reliability, and release evidence | [Engineering principles](Web%20app%20development/engineering-principles.md) |
| [Mobile development](Mobile%20development/README.md) | React Native architecture, offline behavior, account isolation, native UX, device QA, and distribution | [Engineering principles](Mobile%20development/engineering-principles.md) |

## Three useful things to take away today

1. **Make `AGENTS.md` a map.** Keep durable boundaries and reading routes at the root. Put detailed rules in focused steering documents. Start with the [web template](Web%20app%20development/templates/AGENTS.md) or [mobile template](Mobile%20development/templates/AGENTS.md).
2. **Test the boundary you changed.** A label fix, an authentication change, and a database migration need different evidence. See [web verification](Web%20app%20development/testing-and-release.md) and [mobile verification](Mobile%20development/testing-and-release.md).
3. **Name the state precisely.** A local build, a deployed service, an installed app, a submitted release, and store approval are separate outcomes. Use the [web release record](Web%20app%20development/templates/release-evidence.md) or [mobile release record](Mobile%20development/templates/release-evidence.md).

## How to use this collection

- Read the relevant folder's overview, then the guide for your current problem.
- Copy a template into your own repository and replace its example paths with real, maintained documents.
- Give your coding agent the relevant instructions and a concrete completion condition.
- Keep only the rules your team can own, apply, and verify.

The web examples draw on a Next.js/TypeScript application with backend services. The mobile examples draw on a bare React Native application with native iOS and Android projects. Those are the reference contexts, not requirements for every project.

## A living collection

The first edition focuses on web and mobile development. More examples and lessons will be added as the collection grows. [Contributing](CONTRIBUTING.md) explains the format; [Sources and adaptation](SOURCES.md) explains where the guidance came from; [Changelog](CHANGELOG.md) records additions.

These are public adaptations of project practices. They describe ways of working, not a claim that every feature has passed every check. Product source code, private operating instructions, credentials, customer data, and deployment identifiers are excluded.

Documentation and original templates are available under the [MIT License](LICENSE).
