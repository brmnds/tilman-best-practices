# Architecture and contracts

## Choose boundaries you can explain

A module or service should own a coherent responsibility. In the source project, the web application, backend services, shared packages, infrastructure, and contracts are organized together where practical. Keep the dependency direction clear even when code shares a repository.

Separate UI composition from business decisions, data access, and infrastructure. A component should not invent its own permission rules or bypass the shared transport layer.

## Start cross-boundary work from a contract

Use the maintained contract that suits the boundary: runtime schemas, shared types, OpenAPI, an event schema, or a protocol manifest. Do not create a second contract merely to say the project is contract-first.

For an API change, define:

- request and response shape, including null, missing, and empty values;
- authenticated identity, resource ownership, roles, and entitlement checks;
- validation and error semantics;
- retry and idempotency behavior;
- compatibility with existing clients and the rollout order.

Generate clients when generation is already the maintained source of truth. Keep server validation and client assumptions aligned. A cast or generic type parameter does not prove that a network payload is valid.

## Keep one owner per lifecycle

One layer should own an operation's transport, retry policy, canonical write, and recovery. UI, proxy, worker, and model tool must not independently retry or persist the same intent without a coordinated contract.

For example, if the API client performs bounded retries, adding automatic retries at both the query and mutation layers can multiply requests. Retry only safe operations and preserve the same idempotency key for the same logical write.

## Configuration and infrastructure

Keep secrets out of code and tracked configuration. Separate environment-specific values from application logic. Build immutable artifacts and use the tracked infrastructure definition for the owning service.

An infrastructure file is desired state, not proof that its state file matches the live system. Verify identity, state ownership, drift, and the exact plan before applying a change. Never use a broad infrastructure apply as a test.

## Compatibility before cleanup

When an interface changes, keep old and new clients compatible during rollout or provide a deliberate migration path. Deploying the server does not prove every mobile installation has updated. Remove compatibility code only after verifying that the old behavior is no longer required.

See [data migrations](data-and-migrations.md) and [mobile parity](../Mobile%20development/templates/feature-parity.md).
