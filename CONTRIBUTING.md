# Contributing

Summary
How to propose changes to The Iridium Road. Issues and pull requests are
proposals, not merge promises. Open a design issue before large work. Sign off
commits (DCO).

## Before contributing

Thank you for considering a contribution.

The project uses a maintainer-led, contribution-friendly model. Changes may be
revised, partially incorporated, reimplemented, deferred, or declined based on
scope, architecture, compatibility, quality, testability, and maintenance cost.

Open a design issue before substantial work on public interfaces, architecture,
dependencies, hardware support, major refactoring, or workload-specific
subsystems—so you do not spend a month on something that cannot land upstream.

AI and machine learning applications and examples are welcome. Infrastructure
stays workload-neutral. Changes that make one workload category the governing
assumption of the core stack are unlikely to be accepted.

Also read:

- [GOVERNANCE.md](GOVERNANCE.md) — who decides
- [PROJECT_SCOPE.md](PROJECT_SCOPE.md) — in and out of scope
- [profile/ARCHITECTURE.md](profile/ARCHITECTURE.md) — component boundaries

## Pick the right repository

```text
Kernel / transport / capabilities / driver observability → Carbon-XDNA
Artifact compile / optimize / construct → Steel
  (public component; org repo after v0.1.0 gate —
   docs/operations/STEEL_V0_1_0_GATE.md)
Runtime / scheduling / dispatch / APIs / compile orchestration → Diamond-accel0
Monitoring / diagnostics / profiling → observability tools (e.g. NPUTOP when published)
```

If unsure, open an Issue describing the problem and which layer you think owns it.

## Design issues first (substantial work)

Open a design issue before implementation for:

- Public API or ABI changes
- Kernel or firmware interface changes
- Architecture changes or new components
- New hardware targets
- New dependencies
- Repository-wide refactors
- Workload-specific subsystems
- Changes affecting compatibility or security

Small bug fixes, docs, tests, and narrowly scoped optimizations may go directly
to pull requests. Prior alignment does not guarantee a merge.

## Maturity expectations

Repositories state status near the top of the README (`Experimental`,
`Developer Preview`, `Beta`, `Stable`, `Archived`, `Planned`, or
`In development`). Match testing expectations to that status. Experimental
components may break without ceremony.

## Pull requests

- Prefer PRs for meaningful architectural changes, including from maintainers.
  Only maintainers merge into protected branches.
- Keep changes focused; explain why in the description.
- Include a test plan (what you ran; hardware/Fedora/kernel when relevant).
- Note license/provenance if you touch vendored or upstream-derived code
  ([docs/operations/LICENSE_AND_PROVENANCE.md](docs/operations/LICENSE_AND_PROVENANCE.md)).
- Follow the [Code of Conduct](CODE_OF_CONDUCT.md).

Maintainers may edit, refactor, squash, reorganize, or partially incorporate
accepted work. Attribution does not promise verbatim preservation.

## Developer Certificate of Origin (DCO)

This project uses the [Developer Certificate of Origin](https://developercertificate.org/).
Each commit must include:

```text
Signed-off-by: Your Name <your.email@example.com>
```

```bash
git commit -s -m "Your message"
```

Sign-off means you have the right to submit the work under the applicable
license(s). No CLA is required at this time.

## Issues

Use templates when available. File on the repository that owns the layer.
Support is via Issues; see [SUPPORT.md](SUPPORT.md).

## Security

Do not file vulnerabilities as public Issues. Use private vulnerability
reporting. See [SECURITY.md](SECURITY.md).

## Maintainers

Ops checklists (bootstrap, migration, security baseline, releases) live under
[docs/operations/](docs/operations/). They do not authorize live org changes by
themselves.
