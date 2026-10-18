# Offline and sync

## Define what “saved” means

A spinner should reflect the operation the user is waiting for. The server may have accepted a write while a local projection is still busy. Those are related but distinct states.

For a feature designed to work offline, a save can settle when the backend confirms success **or** the intent has been safely admitted to the durable queue. Tell the user when it is queued rather than synchronized. A failed enqueue is a real failure.

For an online-required operation, only the confirmed server result settles the operation. Never imply that an upload, purchase, or server-only action has been queued unless its product contract actually supports that behavior.

## Classify writes

| Class | Settlement | Offline policy |
| --- | --- | --- |
| UX-critical, offline-capable | Server acknowledgment or verified durable admission | Queue when not confirmed online; bounded live attempt otherwise |
| Online-required | Confirmed server success/failure | Clear unavailable state; no invented queue fallback |
| Replay-safe background write | According to its domain contract | Queue only when replay and ownership are safe |

Cache warmup and local projection are follow-up persistence work, not remote mutation classes.

## Keep one durable pipeline

Reuse the existing queue, ordering, idempotency, coalescing, and reconciliation rules. A second queue hidden in one screen creates competing recovery paths.

Keep the same idempotency key across attempts for the same intent. Distinguish a transport failure with an uncertain server outcome from an explicit validation or permission rejection. Do not queue every error indiscriminately.

Centralize bounded retries and avoid multiplying transport retries with automatic query retries. Queue replay should isolate unrelated failures while preserving ordering for dependent operations. Preserve conflicts and unsynchronized user data for reconciliation.

## Fence the initiating account

Capture owner and authentication-generation context before asynchronous preparation. Validate it before transport, durable admission, replay, and publication of success. Signing out and returning to the same account must still invalidate a stale operation from the earlier session.

Do not assign legacy queue entries with unverifiable ownership to whichever user is currently signed in. Preserve them for explicit reconciliation.

## Settle first, project safely

After server success or durable queue admission, release the user-facing pending state. Perform the required local read-model projection through an observable background path with retry/recovery. Do not wait for a locked local database before closing a successful save flow.

The exception is an operation whose product contract is the local durable write itself. That write must actually succeed before the app claims it is safe.

Likewise, a successful network read with valid data remains a successful read even if follow-up local projection fails. Report a persistence-health problem separately instead of inventing an API failure.

In a React Query implementation, ensure offline-capable mutations can actually execute their local admission path while offline. In the source project this uses `networkMode: 'always'`; otherwise the query library can pause the mutation before enqueue runs. Adapt this to the installed version and project implementation.

## Verify the complete lifecycle

Cover online success, offline admission, process restart before replay, reconnect, duplicate replay, conflict, enqueue failure, projection failure, and account switching during an in-flight save.

Downloading once is insufficient offline evidence. Verify rendering and playback after relaunch, then a disconnected cold launch, and finally logout/account cleanup for private content. Record results in the [device QA template](templates/device-qa.md).
