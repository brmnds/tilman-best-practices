# Native UX and dependencies

## Start with the maintained primitive

Before adding a package, identify the exact interaction and inspect existing project components. A selection dialog, keyboard-aware editor, native picker, and chat composer have different ownership needs.

A library can be the simplest choice when it provides accessibility, platform behavior, and lifecycle handling that the project would otherwise need to build. “Fewer dependencies” is a heuristic, not permission to replace a sanctioned component with an incomplete custom one.

## Evaluate the full cost

For a new dependency, review:

- whether the required behavior already exists;
- maintenance and official integration guidance;
- peer dependencies and compatibility with the pinned toolchain;
- native code, build scripts, architecture and platform requirements;
- permissions, privacy, accessibility and lifecycle behavior;
- failure modes, removal cost, and how the affected platforms will be validated.

Keep upgrades scoped. A small UI task should not quietly become a framework migration. Measure performance before adding a complex animation or caching stack.

## Give the keyboard one owner

A managed form dialog should own its available height, focused-input handling, and scrolling. Nesting several keyboard-avoidance mechanisms can double the offsets or trap controls.

Use a screen-owned strategy for full-screen forms and composers, and let operating-system pickers own their native interaction. Fix a local defect at its owner before adding a global keyboard workaround.

## Treat layout as runtime behavior

Check compact and large windows, safe areas, rotation where supported, long content, dynamic text, and the keyboard. Verify that submit, cancel, and recovery controls remain reachable and that focus returns after nested pickers close.

Check platform back/dismiss behavior, screen-reader labels, touch targets, contrast, and user-visible validation. A screenshot with the keyboard closed does not prove an editor is usable.

## Follow the actual project toolchain

Inspect native projects, package scripts, and lockfiles before running commands. The source application is bare React Native and launches through its React Native CLI workflow. A different project may deliberately use another setup.

When native configuration changes, build the affected target and inspect the produced artifact. A JavaScript test that searches a project file proves only that text exists.
