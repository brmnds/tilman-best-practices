# Testing and release

## Choose checks by the boundary changed

The source web project uses a risk-based local verification matrix. A hosted green badge alone does not establish release readiness. The transferable rule is to record the relevant checks and exact deployment evidence, wherever a team runs them.

| Risk | Typical change | Useful evidence |
| --- | --- | --- |
| 0: Documentation | Prose, diagrams, inert examples | Exact diff, whitespace, links; verify operational commands if edited |
| 1: Contained behavior | One page, form, or bounded endpoint | Focused behavior tests, affected static checks, targeted UI check; build when runtime boundaries require it |
| 2: Shared boundary | Auth, permissions, middleware, shared client, AI persistence | Characterization, allow/deny, recovery/retry/concurrency tests, appropriate broader regression and build |
| 3: Consequential operation | Schema, IAM, billing, delivery, private media, deletion | Exact reviewed change, authority, preflight/dry run, recovery plan, postconditions, synthetic canary and observation |

These are decision aids, not a checklist that accumulates every test at every tier. Never reduce a critical check merely to move faster.

## Prove behavior

Test the result through the relevant boundary. A source-text check cannot prove that a login recovers or a button works. Include failure, cancellation, replay, and unauthorized cases where they matter.

Use labelled synthetic data. Do not create real purchases, send customer communications, delete real accounts, or change real roles merely to test a flow.

## Run a stable final matrix

Use focused checks for fast feedback while implementing. Once the executable candidate is stable, preflight tools and dependencies, combine overlapping suites, and run one final matrix.

Record source identity, dependencies/configuration, environment, exact command, and result. Reuse deterministic evidence while those inputs remain unchanged. If a later commit changes only prose, inspect the changed paths and record why the previous build remains relevant.

Recheck mutable state at each new push, deployment, migration, or activation. Old canary results do not prove a new deployment is healthy.

## Release in explicit stages

1. Review the complete intended commit range and exclude unrelated work.
2. Run the repository's public-data/secret checks and applicable quality gates.
3. Verify the exact remote, environment, project, and authority before publication or deployment.
4. Verify the deployed source identity and build result.
5. Exercise the affected synthetic journey and inspect safe logs/alarms.
6. Record remaining gaps and a recovery decision if a gate fails.

A preview may be useful for hosting or review behavior, but it cannot prove production-only configuration or database access. Choose observation time according to how harm could emerge; do not add an arbitrary long wait to every release.

## Report states precisely

Use statements such as: "Focused tests and local build passed; deployment pending" or "The named commit is deployed; the synthetic save/reload canary passed."

Keep local source, tests, build, preview, production deployment, and production acceptance separate in the [release record](templates/release-evidence.md).
