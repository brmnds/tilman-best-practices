# Account isolation and private media

## Use the right storage boundary

Keep session secrets in platform secure storage. Non-sensitive preference storage is not an authentication vault. Owner-scoped local entity storage needs explicit retention, cleanup, and access controls; selecting SQLite alone does not establish encryption or privacy compliance.

Keep API credentials on the backend. The mobile client must not carry provider secrets or connect directly to the production database.

## Bind asynchronous work to its owner

Cancellation on navigation is useful but insufficient. A request, refresh, replay, or download can outlive an account switch. Capture the initiating owner and auth generation, propagate cancellation, and validate ownership before accepting or publishing the result.

On logout/account change, cancel old work and clear or isolate private cache, pending data, downloaded files, temporary previews, and queued intent according to the current ownership contract. Fail closed when private cleanup cannot be confirmed.

## Separate media resolution from download

For private media, persist a stable owner-authorized reference rather than an expiring signed URL. Resolve it through authenticated application transport, validate the transient target, then fetch media through a separate credential-free download path.

Application session headers, cookies, and tokens belong only on the trusted resolver hop. Do not forward them to an arbitrary storage or CDN URL. Validate permitted schemes, hosts and URL structure according to the feature's contract.

Signed targets remain transient: exclude them from query caches, local databases, diagnostics, analytics, and logs. Store local bytes only in the approved owner namespace and apply the intended retention/cleanup policy.

## Preserve explicit denial

Do not silently fall back to an older public media field after an authenticated resolver denies access. Distinguish an absent new field from an explicitly null or invalid field. Compatibility must not bypass a newer privacy contract.

Treat authentication recovery, permission denial, not-found, malformed response, cancellation, and network failure according to their defined semantics.

## Verify with two synthetic owners

Start a private read or download as owner A, switch to owner B before completion, and confirm B never receives A's state or bytes. Check denied access, resolver validation, cleanup, cold launch, and offline playback only where that feature supports it.

Device diagnostics and screenshots should establish the result without exposing tokens, signed URLs, recordings, or unrelated personal content.
