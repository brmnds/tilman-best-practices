# Example web project agent guide

> Template for your own repository. The paths below are examples to create or replace. This file describes the example project, not the public best-practices collection.

## Purpose and scope

Describe the product, supported runtime, repository boundaries, and current task boundary here. Preserve existing functionality and unrelated working-tree changes.

## Start here

1. `governance/README.md`: current guidance index and document status.
2. `governance/steering/engineering-principles.md`: broad design rules.
3. The narrowest applicable steering document and current contract.
4. The owning route, package, service, or infrastructure README.

## Authority

Applicable platform instructions and safety requirements remain in force. Within the project, follow explicit in-scope user direction, current owning domain guidance, current specifications, broad standards, and supplementary runbooks in that order. Label archives and proposals as non-authoritative. Resolve material conflicts before changing behavior.

## Task routing

| Change | Required context |
| --- | --- |
| Page or form | Owning route README, design system, testing standard |
| API | Owning contract, authorization rules, validation/error policy |
| Auth or private data | Security rules, owner/role matrix, recovery contract |
| Database | Current schema contract, migration procedure, live-state preflight |
| AI feature | Identity/tool contract, persistence owner, eval fixtures |
| Deployment | Release runbook, current target identity, verification standard |

## Boundaries

- Derive authenticated identity server-side and enforce resource ownership.
- Validate network and tool inputs at runtime.
- Keep credentials, private data, and raw sensitive logs out of tracked files and reports.
- Treat a cross-repository dependency as read-only unless changes there are authorized.
- Verify mutable target, role, schema, and deployment facts at the action boundary.
- Respect the requested scope for local changes, push, deployment, migration, and external actions.

## Completion

Select the smallest credible test matrix for the affected risk. Record source identity, exact commands/results, UI evidence where needed, and any remaining release steps. Update the owning contract or runbook with behavior changes. Do not equate a local build with deployment or acceptance.
