# Example mobile project agent guide

> Template for your repository. Create or replace the example paths and adapt the toolchain to your application. This is not the operating guide for the public collection.

## App and repository scope

Describe the app, owned iOS/Android targets, supported companion targets, and shared backend reference here. Preserve functionality and unrelated edits. Treat sibling repositories as read-only unless their changes are in scope.

## Current authority

This file owns repository boundaries and required process. `governance/README.md` identifies current domain standards. Current feature contracts define intended behavior; code, tests and configuration establish mechanical facts. Label plans, archives and snapshots as historical. Higher-priority platform instructions and applicable safety requirements remain in force.

## Required routing

| Task | Read |
| --- | --- |
| Shared feature | Owning screen README, shared product/API contract |
| State or fetching | Data ownership and query-key standard |
| Write or offline behavior | Settlement, durable queue, conflict and replay rules |
| UI interaction | Current component, modal, keyboard and design guidance |
| Auth/private data | Session contract, secure storage and identity cleanup |
| Dependency/native change | Compatibility guidance, lockfile, build runbook |
| Release | Metadata source, signing/artifact verifier and destination runbook |

## Implementation boundaries

- Preserve shared business rules while adapting interaction for mobile.
- Give each async lifecycle one owner and propagate cancellation.
- Bind query, optimistic, queue, projection and media work to the initiating account.
- Reuse the existing durable pipeline. Never call an online-required action queued.
- Keep secrets out of preference storage, tracked files and diagnostics.
- Verify actual toolchain, device and environment before relying on old commands.

## Validation

Select the smallest credible profile for the changed risk. Record exact static/test commands, native artifacts, platform/runtime checks and gaps. Add both-platform validation when shared native or known platform divergence requires it. Do not rerun app builds solely for a prose change.

## Distribution and completion

Follow the named authority for local work, archive/bundle, upload, submission and rollout. Verify the actual app ID, version/build and destination. Keep source, build, install, device QA, upload, review and availability evidence separate. Update the owning README or contract with behavior changes.
