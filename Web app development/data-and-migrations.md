# Data and migrations

## Ownership belongs in the access path

Derive identity from the authenticated server context. Check the resource's owner, role, sharing rules, and entitlement where applicable. A client-provided user ID, resource ID, or model argument is not authorization.

Use parameterized queries and least-privilege database access. Test both allowed access and another user's denied access. The source project's application-level authorization is one implementation choice; this collection does not prescribe the same database enforcement model for every system.

## Separate three sources of evidence

| Evidence | What it tells you |
| --- | --- |
| Current schema specification | The intended contract |
| Migration file and application ledger | The reviewed change and recorded application |
| Authorized live-schema inspection | What the named environment actually contains |

A migration file in Git does not establish production state. A ledger entry should come from direct verified application, not a scan of historical filenames.

## Prepare a bounded change

1. Inspect the relevant schema, consumers, and current migration conventions.
2. Confirm the live need through the approved read-only path when the task requires it.
3. Write the exact migration with preflight assertions, postconditions, and recovery steps.
4. Check old/new application compatibility and locking or backfill cost.
5. Review the specific target, checksum, rollout order, and authority before applying.

Make idempotency intentional. `IF EXISTS` or `IF NOT EXISTS` must not hide an object with the wrong definition. Verify its required shape.

## Prefer expand, migrate, contract

Add a compatible structure, deploy code that can handle the transition, migrate or backfill with bounded work, verify the result, then remove the old structure in a later change. Define whether rollback is safe after new writes, or whether a forward fix is required.

Application deployment and schema application are separate actions. Keep sensitive activations independently reviewable even when compatible application changes ship together.

## Verify without exposing content

Use constraints, counts, checksums, and synthetic records where they establish correctness. Do not inspect private journals, full billing payloads, or unrelated customer rows for routine debugging. Sanitize error context and retain only the evidence needed for the decision.

After an authorized change, verify postconditions, record its actual application, run the relevant synthetic canary, and inspect safe operational signals. Leave an explicit follow-up for anything that remains unverified.
