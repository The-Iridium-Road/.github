# Release Conventions

Summary
How versions, maturity labels, and changelogs work across Iridium Road repos.
Steel’s first-public-tag criteria are historical in STEEL_V0_1_0_GATE.md.
Current Steel tip is Experimental v0.1.2. Cutting releases and pins are live
actions after explicit approval.

## Version tags

Use SemVer-style tags with a `v` prefix:

```text
v0.6.0
v0.7.0-rc.1
v1.0.0
```

- Release candidates: `vMAJOR.MINOR.PATCH-rc.N`
- Do not recycle or move tags that dependents may have consumed

## Maturity status

Every repository README should state status near the top, using:

`Experimental` · `Developer Preview` · `Beta` · `Stable` · `Archived` ·
`Planned` · `In development`

Current public expectations (update when reality changes):

```text
Carbon-XDNA — Developer Preview, v0.6.0
Steel — Experimental, v0.1.2 — https://github.com/The-Iridium-Road/Steel
Diamond-accel0 — In development, v0.0.3 — heavy development; not release-ready
NPUTOP — Planned; prototype / integration pending
Examples / utilities — Planned category, not a fake repository
```

## Changelog

- [ ] Maintain `CHANGELOG.md` (or equivalent release notes) for core repositories
- [ ] Note breaking changes, hardware/firmware assumptions, and Fedora/kernel
      compatibility when relevant
- [ ] Link release tags to changelog sections when practical

## Steel releases

Published: https://github.com/The-Iridium-Road/Steel

- v0.1.0 — first public compile-only façade (gate:
  [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md))
- v0.1.1 — pinned toolchain Release + `light_steel_forge.sh`
- v0.1.2 — forge hrx FULL packager, XRT guillotine for FULL, LEGAL for hrx,
  CMake embed fix; pair with toolchain-v2026.08.2
  (https://github.com/The-Iridium-Road/Steel/releases/tag/v0.1.2,
  https://github.com/The-Iridium-Road/Steel/releases/tag/toolchain-v2026.08.2)

Product tags and toolchain tags are independent. Consumers pair via
`steel/toolchain.lock`. Depth (STEEL_API, forge README, LEGAL) stays in the
Steel repository—not duplicated here.

## Relationship to live bootstrap

Cutting releases, creating repositories, and pinning them on the organization
profile are live actions. Follow
[ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md) and
[REPOSITORY_MIGRATION.md](REPOSITORY_MIGRATION.md) only after explicit approval
of that phase.
