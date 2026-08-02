# Release Conventions

Summary
How versions, maturity labels, and changelogs work across Iridium Road repos.
Steel’s finite ship gate lives in STEEL_V0_1_0_GATE.md. Cutting releases and
pins are live actions after explicit approval.

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
Steel — In development, pre-v0.1.0; lands in org after Carbon once
  STEEL_V0_1_0_GATE.md passes (before Diamond in landing order)
Diamond-accel0 — Experimental, v0.0.5
NPUTOP — Planned; prototype / integration pending
Examples / utilities — Planned category, not a fake repository
```

## Changelog

- [ ] Maintain `CHANGELOG.md` (or equivalent release notes) for core repositories
- [ ] Note breaking changes, hardware/firmware assumptions, and Fedora/kernel
      compatibility when relevant
- [ ] Link release tags to changelog sections when practical

## Steel v0.1.0

The complete finite gate, ship rule, and post-ship steps live in
[STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md).

No organization Steel repository URL until the gate passes; then ship v0.1.0 and
create under `The-Iridium-Road` when possible. Further polish is v0.1.1 or
v0.2.0—not a reason to delay the first tag.

## Relationship to live bootstrap

Cutting releases, creating repositories, and pinning them on the organization
profile are live actions. Follow
[ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md) and
[REPOSITORY_MIGRATION.md](REPOSITORY_MIGRATION.md) only after explicit approval
of that phase.
