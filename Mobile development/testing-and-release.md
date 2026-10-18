# Mobile testing and release

## Select the validation profile

| Profile | Typical change | Evidence to select |
| --- | --- | --- |
| 0: Documentation | Prose, diagrams, inert examples | Diff, whitespace and references; no native build solely for prose |
| 1: Contained behavior | One screen, utility or hook | Static checks, focused behavior tests, runtime check if interaction needs it |
| 2: Shared behavior | Auth, navigation, transport, persistence or sync | Deduplicated regression across affected consumers, relevant runtime/lifecycle checks |
| 3: Native or consequential | Native dependency, signing, private data, billing or distribution | Applicable lower layers, affected native artifact verification, focused simulator/device checks |

A profile expresses consequence, not an instruction to accumulate every possible suite. A signing-only change does not need unrelated JavaScript tests. A shared native dependency may require both platform builds.

The source app uses local checks rather than hosted check status as its authority. The general lesson is to record what ran and what it proved.

## Freeze the executable candidate

Preflight dependencies, tools, platform availability, and required access before expensive checks. Use focused feedback while developing, then one consolidated matrix after the source is stable.

Record static checks, targeted tests, relevant dependency-cycle checks, native builds, runtime observations, and limitations. Reuse deterministic evidence for unchanged source/configuration/dependencies and relevant environment. Recheck anything a changed input can invalidate.

A simulator is useful for interaction and lifecycle checks. Use a physical device when the risk involves hardware permissions, audio routing, interruption, connectivity, performance, provisioning, or another behavior the simulator cannot establish.

## Keep release states separate

1. **Source ready:** the reviewed change and required documentation are committed.
2. **Locally verified:** the chosen checks passed against the recorded inputs.
3. **Artifact created:** the intended archive/bundle exists.
4. **Artifact verified:** app ID, version/build, source identity, signature, hash, embedding, and symbol relationships match the candidate where applicable.
5. **Installed and exercised:** the actual runtime identity and required journeys were observed.
6. **Uploaded:** the destination accepted the artifact transfer.
7. **Submitted:** a review or release request was explicitly confirmed.
8. **Approved and available:** review and rollout state were verified in the destination.

Symbol-file generation, symbol upload, server processing, and a successfully symbolicated event are also separate observations.

## Respect the named release scope

Local test/build work, distributable artifact creation, external upload, review submission, and production rollout have different consequences. Follow the user's authorized platform, app, version, and destination through its ordinary workflow. Do not silently broaden that scope.

Read version metadata from native project sources. Keep any in-app diagnostics mirror aligned with those sources. Keep signing material and credentials local and private.

## Validate the highest-risk journeys

Use synthetic accounts that match the intended role, subscription, and onboarding state. Cover affected save/reload, session recovery, offline/reconnect, account switching, keyboard/navigation, and permission behavior.

For companion apps or widgets, compile the actual containing and embedded targets. Inspect packaging and test the changed native behavior. A project-file string check cannot substitute for native compilation.

Use the [QA record](templates/device-qa.md) and [release record](templates/release-evidence.md). Report pending device or store acceptance explicitly.
