# AI feature reliability

A useful model response is only one part of an AI feature. Identity, durable state, tools, retries, and recovery need explicit ownership.

## Keep identity outside model control

Authenticate at a trusted application boundary. Forward identity through a verified internal binding and check it independently at each tool boundary. Strip client- or model-selected identity from tool arguments before injecting the authorized identity.

A model may propose a resource or action. The executor must still check ownership, permission, input shape, and the tool allowlist. Do not substitute an unknown or default user when identity is missing.

## Own the canonical conversation

Keep a durable, owner-scoped transcript in an application-controlled store. Provider conversation state can assist continuity, but should not be the sole record when the product requires recovery and auditability.

Choose one canonical writer per accepted turn. A thin proxy, streaming client, worker, and realtime adapter must not each write competing copies. Define which final events may become canonical records; partial streaming deltas are transport state.

Bound history retrieval according to the actual context and cost contract. Keep the implementation, tests, and documentation aligned when that policy changes.

## Design retries around user intent

Give each accepted turn and material tool write a stable idempotency identity. Retrying the same intent must not duplicate a task, charge, or record. A deliberately repeated user action must remain distinct from replay of the previous action.

A dropped stream does not prove the server cancelled. Recover the canonical result using the original operation identity before creating a new write.

## Version and evaluate changes

Version prompts, model configuration, response schemas, and tool contracts in their owning sources. Use regression fixtures for expected behavior, invalid arguments, denial paths, interruption, and duplicate replay. Include human review for subjective quality, plus latency and cost checks appropriate to the feature.

Verify current provider capabilities and API instructions during implementation. This guide deliberately avoids model names and version-specific payloads.

## Observe safely

Propagate a correlation ID across the request, runtime, and tool hops. Record safe metadata such as tool name, outcome, duration, usage, and error category. Exclude tokens, private inputs, signed URLs, raw recordings, and hidden chain-of-thought from diagnostic logs.

Keep consequential actions behind the product's explicit confirmation and authorization contract. The model's confidence does not replace that contract.

## Acceptance example

For an AI task-creation feature, prove that the correct owner can create a synthetic task, another owner cannot read it, an identical replay creates no duplicate, an interrupted client can recover the result, and the trace explains the outcome without exposing private content.
