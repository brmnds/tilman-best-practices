# Engineering principles

## Keep complexity proportional to the problem

Use the simplest design that meets the actual requirement. KISS, DRY, and YAGNI are decision aids: avoid premature abstractions, share logic when it reduces maintenance, and add infrastructure only for a demonstrated need.

Start with modules in an understandable repository. Split a service when runtime needs, latency, isolation, or ownership justify the operational cost. A monorepo is a useful default in the source web project; it is not a prerequisite for applying these practices.

## Preserve existing behavior

Fix the root cause. Before deleting a helper, UI section, or data-processing path, trace its consumers and the product behavior it supports. Removing a feature to make an error disappear changes the task and needs an explicit product decision.

Keep unrelated edits intact. A busy working tree is a reason to isolate your change, not permission to clean up another person's work.

## Put authority in one maintained place

Use one authoritative source for each contract, design-token set, data model, or operational procedure. Link to it from other documents. Repeated copies become different rules over time.

Distinguish intended behavior from implemented behavior and live state. A specification defines the contract; code and tests describe implementation; live checks establish deployment and configuration facts.

## Build for the next maintainer

Separate presentation, domain logic, state, transport, and infrastructure. Prefer composition and small functions to deep inheritance. Make invalid inputs and failure states explicit. Use strict types and validate runtime boundaries; TypeScript alone cannot validate an incoming request.

Document the decisions that would otherwise need rediscovery. Feature READMEs explain ownership and use; architecture decision records explain consequential tradeoffs.

## Measure before optimizing

Inspect the slow journey, expensive request, or failing operation before introducing a cache, abstraction, or dependency. Agree on a baseline and a useful target. Check whether the change improves the user's experience and whether it adds a new correctness burden.

## Match verification to consequence

A text change and an authorization change need different checks. Prove the changed behavior, its important failure mode, and its data boundary. Use synthetic fixtures and metadata rather than private customer content.

For each review, ask:

1. Does this fit the architecture and preserve the product contract?
2. What evidence verifies it?
3. Could the result be simpler?

Continue with [agent context](agent-context-and-steering.md) and [verification](testing-and-release.md).
