# Agent guide for this collection

## Purpose

Maintain a public, reader-friendly collection of Tilman Resch's engineering practices. This repository contains documentation and templates, not the LuminaOS application.

## Start here

Read `README.md`, `CONTRIBUTING.md`, and `SOURCES.md`. Then read the relevant development folder's overview and the exact document being changed.

## Structure

Keep the two top-level topic folders: `Web app development/` and `Mobile development/`. Put copyable examples under each topic's `templates/`. Add further top-level topics only when requested by the maintainer.

## Writing and source boundaries

- Explain the problem, the practice, and how to verify it. Keep project-specific choices distinguishable from transferable principles.
- Use plain English and concrete examples. Avoid the em dash character.
- Treat templates as examples to adapt, not instructions to execute against the source product.
- Maintain one authoritative explanation per concern and link to it from related guides.
- Do not copy private repository contents wholesale. Publish only deliberately reviewed adaptations.
- Exclude credentials, personal paths, private contact details, account inventories, internal infrastructure identifiers, private resource links, customer records, and raw logs.
- Do not make claims about current provider APIs or versions without verifying their official documentation. Prefer version-independent principles here.

## Verification and delivery

Review the complete diff, check relative links and whitespace, and scan all proposed public files for sensitive material. Verify that templates link to real collection documents or clearly describe paths readers must create. Runtime tests and app builds are unnecessary for prose-only changes.

Preserve unrelated work. A documentation edit does not by itself authorize a push or other external publication. When publication is requested, verify the exact repository, intended visibility, commit, and remote file tree before reporting completion.
