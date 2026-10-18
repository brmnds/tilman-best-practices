# Agent context and steering

An agent works more reliably when it can discover the right instructions quickly. A root file that contains every historical command and implementation detail becomes hard to trust.

## Give each document a job

| Document | Owns | Avoid putting here |
| --- | --- | --- |
| `AGENTS.md` | Durable boundaries, authority rules, reading order, task routing | Full runbooks, live inventories, dated incident history |
| `governance/README.md` | Map of current guidance and its status | A second copy of every rule |
| `governance/steering/` | Engineering policy and domain decision rules | Unlabelled historical snapshots |
| `governance/specs/` | Product, API, schema, and behavioral contracts | Credentials or assumptions about live rollout |
| Feature/service `README.md` | Ownership, local structure, setup, behavior | Global policy duplicated across features |
| `docs/` | Runbooks, operational evidence, incident lessons | Implicit authority just because a file exists |
| Reusable skill | A repeatable workflow with inputs and verification | A competing product specification |

These paths are a suggested structure, not required tooling.

## Keep the root map short and actionable

A useful `AGENTS.md` explains what the repository is, what may be changed, how conflicting instructions are resolved, what to read for each change, and what evidence counts as completion.

Route by task: an API change needs the owning contract and authorization guidance; a page change needs the route README, design guidance, and testing standard. Neither needs every historical document in the repository.

Declare your document hierarchy explicitly. Higher-priority platform instructions and applicable safety requirements still apply. Within project guidance, identify which current domain documents own their concerns and which files are supplementary. A historical document must not silently override a current contract.

## Separate stable rules from mutable facts

Stable rules include preserving unrelated work, deriving identity server-side, and using scoped verification. Mutable facts include deployment targets, active accounts, tool availability, cloud roles, and live database schemas. Verify mutable facts at the action boundary.

Mark superseded documents and point to their replacements. If an old example conflicts with the current owning standard, update or label the example rather than letting both look authoritative.

## Keep skills canonical

Maintain one source for reusable skills and distinguish that source from installed copies. Compare divergent versions before synchronizing. Do not silently overwrite local improvements or duplicate managed third-party skills into a personal registry.

A skill should define its trigger, inputs, steps, boundaries, and verification. The product specification continues to own product behavior.

## Example workflow

Request: fix a form that loses a draft after navigation.

1. Read the root map and the form's owning README.
2. Find the persistence and account-isolation contract.
3. Reproduce with synthetic data and trace the lifecycle.
4. Make the smallest coherent fix, including contract documentation if needed.
5. Test navigation, restoration, and account switching at the affected boundary.
6. Report the evidence and any remaining deployment work.

Use the [root-file template](templates/AGENTS.md) as a starting point. Its example paths must be created or replaced before adoption.
