# Frontend quality

## Show useful content promptly

When valid cached data exists for the authenticated user, keep it visible while refreshing in the background. Reserve a blocking loader for a surface with nothing useful to render. Show stale or refresh-failure feedback without replacing a usable screen with an empty one.

Distinguish empty results from failed reads. A malformed response should surface a contract error; converting it silently into an empty list tells the user the wrong story.

## Make caching explicit

Use one query-client owner and maintained key factories. Include account identity in user-specific cache keys. Scope optimistic updates, rollback, invalidation, and logout cleanup to the same owner.

Client state reuse, server-side caching, and HTTP caching are separate decisions. Verify the framework's actual behavior instead of copying defaults from an older version. The source web project explicitly keeps API responses uncached at the server boundary while using client query state for authenticated reuse. Do not turn that into a global shared cache of private data.

Prefetch on a meaningful navigation signal such as hover, focus, or touch. Bound speculative work and respect constrained connections. Load the important content first and defer lower-priority images and modules.

## Make writes honest

Disable duplicate submission only for the appropriate pending window. Use optimistic feedback where rollback is meaningful. A mutation must not retry globally unless the operation is safe to replay with a stable idempotency key.

Preserve form input after recoverable failures. Distinguish validation problems, expired sessions, permission denials, and unavailable services so the user gets an actionable next step.

## Treat visual quality as behavior

Use design tokens for color, spacing, type, and component states. Check compact and large viewports, long labels, empty states, dense content, and error messages. A successful API response does not establish that the form remains usable.

Verify keyboard navigation, visible focus, dialog focus return, semantic controls, meaningful labels, contrast, and zoom. Prefer the project's maintained accessible primitives to a custom interaction that recreates these responsibilities.

## Measure a real journey

Choose a representative device/network and record a baseline before optimizing. Inspect navigation responsiveness, content arrival, layout shifts, and interaction delay. Keep performance targets explicit and project-specific.

A focused browser check should cover the changed interaction, its loading/error states, affected viewports, keyboard behavior, and unexplained console or network errors. Use [release evidence](templates/release-evidence.md) to distinguish local browser results from deployed acceptance.
