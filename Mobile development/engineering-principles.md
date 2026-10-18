# Mobile engineering principles

## Use platform-appropriate simplicity

Prefer an existing maintained project primitive or a suitable built-in API before adding another dependency. The cheapest component to type is not always the cheapest component to maintain: accessibility, keyboards, native builds, and lifecycle behavior are part of its cost.

A simple selection menu rarely needs a new animation stack. At the same time, replacing an established accessible dialog with a raw modal can discard years of fixes. Evaluate the current system, not only dependency count.

## Preserve the shared product contract

Research the corresponding web feature when behavior is shared: fields, categories, calculations, validation, permissions, entitlements, and backend responses. Adapt navigation, layout, gestures, and feedback for mobile.

Mobile should preserve the relevant capability without copying DOM components or every desktop interaction. Clearly mobile-only work does not require unrelated web research.

## Give each lifecycle an owner

Screens compose. Focused controllers own requests, cancellation, pending/error state, and recovery. Transport owns network policy. The durable pipeline owns queued intent and replay. Presentation sections receive typed data and callbacks.

Moving a monolith behind a tiny wrapper does not improve ownership by itself. Avoid splitting one asynchronous operation across several hooks merely to reduce file length.

## Design for interruptions

Apps background, networks degrade, credentials expire, keyboards resize screens, and users switch accounts. Treat these as normal states. A save or download must remain bound to its initiating owner throughout its lifecycle.

Useful cached content should stay available during a recoverable refresh failure. Offline capability must be explicit per domain; a cached list does not establish that every operation works offline.

## Keep native changes deliberate

Review peer dependencies, lockfiles, native setup, architecture compatibility, signing implications, and both platform build paths before adopting a native dependency. Avoid broad upgrades or downgrades as a shortcut to fixing one feature.

## Verify at the right layer

JavaScript tests, native compilation, simulator interaction, physical-device behavior, and store processing answer different questions. Choose the checks the changed boundary needs and record gaps accurately.

Ask during review: does this preserve the product contract, fit the platform, have credible evidence, and remain as simple as the requirement allows?
