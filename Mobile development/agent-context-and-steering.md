# Mobile agent context and steering

Use the same [documentation roles](../Web%20app%20development/agent-context-and-steering.md) as a starting point, with mobile-specific ownership made explicit.

## What the root file should establish

- Which app, native targets, and platforms this repository owns.
- Which toolchain launches and builds it.
- Which sibling repositories are reference-only for the current task.
- Where current architecture, state, offline, UI, auth, and testing guidance lives.
- What local validation, artifact creation, distribution, and rollout authority mean.
- How conflicting current documents and historical material are handled.

The source mobile project treats its root `AGENTS.md` as repository operating authority and promotes current domain documents through its governance index. Other projects can choose a different explicit hierarchy. Consistency and discoverability matter more than copying a hierarchy verbatim.

## Route to the owning standard

| Task | Read first |
| --- | --- |
| Shared feature | Mobile screen contract and matching backend/web business behavior |
| Data screen | Query keys, response normalization, durable-read ownership |
| Save or sync | Write classification, settlement, replay and conflict rules |
| Dialog or form | Current modal, keyboard, design-system and accessibility guidance |
| Auth/account switch | Session contract, secure storage, identity teardown and owner fencing |
| Native dependency | Current compatibility/install instructions and owning build runbook |
| Release | Native metadata source, signing, artifact verifier and destination runbook |

Do not copy live versions, signing identities, device identifiers, or credentials into the root map. Resolve them when the task reaches that boundary.

## Keep cross-repository work scoped

Read the backend contract when needed, but do not silently edit the backend to make a mobile feature pass. If that work is outside scope, prepare a precise handoff: context, code locations, required behavior, compatibility, verification, risk, and remaining work.

A handoff draft is distinct from sending it or starting work elsewhere.

## Make completion observable

A task report should distinguish source changes, automated checks, native builds, installed identity, runtime observations, upload, submission, review, and rollout. Preserve passing evidence when the relevant inputs are unchanged, and recheck mutable destination state at distribution time.

Copy the [mobile AGENTS template](templates/AGENTS.md), then replace its example paths and rules with maintained project guidance.
