# Contributing and extending the collection

Keep additions practical enough for someone arriving from LinkedIn to use without access to LuminaOS.

## A useful contribution

Each guide should answer:

1. What problem does this practice solve?
2. What should someone do differently?
3. What tradeoff or limitation matters?
4. What evidence would show that it works?

Prefer a short explanation and a concrete example. Label illustrative snippets and local conventions. Avoid universal numeric thresholds without a documented reason.

## Adding a practice

1. Choose the web or mobile folder. If both benefit, keep the shared explanation in one place and cross-link it.
2. Check for an existing guide before creating a competing explanation.
3. Separate principles, required project rules, operational procedures, and historical lessons.
4. Add an entry to the topic overview and update `CHANGELOG.md`.
5. Update `SOURCES.md` when new source material contributes a practice.
6. Review the diff, links, and public-data boundary before publication.

## Templates

Use generic paths and synthetic examples. Explain which files the adopter must create. Do not include executable production commands, real identifiers, secret-store locations, provider credentials, or private links.

## Public material only

Do not submit private source code, customer data, journal content, authentication material, screenshots containing private information, internal cloud identifiers, or private operational runbooks. A private source document can inform an original public adaptation without being copied into this repository.

Keep external dependencies and automation out of the collection unless a concrete use case requires them. Documentation improvements do not need an application build pipeline.
