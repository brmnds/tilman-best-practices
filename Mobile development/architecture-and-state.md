# Architecture and state

## Separate responsibilities

| Concern | Typical owner |
| --- | --- |
| Screen composition and route inputs | Screen shell |
| One asynchronous feature lifecycle | Focused controller or hook |
| Server reads and active optimistic state | Query/mutation layer |
| Request validation and normalization | API service boundary |
| Retry, authentication recovery and cancellation | Shared transport |
| Durable offline entities | Owner-scoped local database/read model |
| Replayable intent | Existing durable-write pipeline |
| Tokens/session secrets | Platform secure storage |
| Small non-sensitive preferences | Preference storage |

These roles matter more than the exact library names. In the source app, React Query coordinates server state, SQLite supports migrated offline domains, and secure storage protects authentication material.

## Keep screens composable

Organize by feature. A screen composes sections and typed actions. Presentation sections should not reach into transport, query clients, global stores, or playback engines when the composition owner can pass the required values.

Keep startup recovery, app-resume handling, and heavy derived state out of large screen bodies. Stabilize callbacks, registration metadata, and empty defaults when their identity can trigger effects. Normal render churn must not restart network recovery.

Check dependency direction and runtime import cycles. Type-only dependencies are different from runtime cycles; a new abstraction that introduces a cycle has not simplified ownership.

## Validate before caching

Normalize supported legacy response shapes at the API boundary. An empty valid collection may become `[]`; malformed, unauthorized, or ownership-mismatched data must remain an error.

Cache one documented shape per query key. If a value contains data and metadata, optimistic updates and rollback must preserve both. Update only range keys whose interval actually contains the changed entity.

## Scope every user-specific layer

Include owner identity in query keys and bind transport to the expected owner. Use the same owner for optimistic snapshots, durable projections, queue entries, invalidation, and rollback.

Cancel old queries and remove or isolate old state on logout/account switch. Never relabel the previous account's data as the new owner's cache. Account identity checks must cover operations that were already in flight.

## Keep startup useful

Render valid local content immediately when the domain supports restoration. Refresh in the background. App-shell access and navigation readiness should not depend on every screen query succeeding.

Document which domains have durable offline support, bounded persisted cache, or best-effort stale content. These are different product guarantees. Continue with [offline and sync](offline-and-sync.md).
