# Project Governance

Summary
Who decides what lands in The Iridium Road. Maintainer-led, contribution-friendly
governance for general-purpose NPU computing on Linux. Contributions are
proposals, not merge entitlements.

## Project direction

Make supported NPU hardware programmable, observable, recoverable, and useful as
a general-purpose Linux compute resource.

No workload category—including AI, ML, media, or any single application—may
define the architecture. Those workloads may be supported as consumers of the
platform. See [PROJECT_SCOPE.md](PROJECT_SCOPE.md).

The lead maintainer owns architectural direction, scope, releases, component
boundaries, and long-term maintainability.

## Contributions

Issues, design proposals, pull requests, tests, docs, and other work are welcome.

A submission is a proposal for inclusion, not a guarantee. It may be:

- Accepted substantially as submitted
- Revised collaboratively
- Reimplemented to fit the architecture
- Incorporated only in part
- Deferred
- Declined as out of scope
- Superseded by another implementation

Decisions weigh:

- Alignment with mission and architecture
- Correctness, security, and recoverability
- General applicability
- Compatibility and maintenance cost
- Testability on supported hardware
- Effects on public interfaces and component boundaries
- Available maintainer capacity

Technically sound work can still be declined for scope or unsustainable
maintenance. “I cannot responsibly maintain this” is a valid reason.

## Design coordination

Discuss substantial work in an issue before implementation:

- Public API or ABI changes
- Kernel or firmware interface changes
- New architectural components
- New dependencies
- Major refactors
- New hardware targets
- Workload-specific subsystems
- Changes affecting security, compatibility, or recovery

Prior discussion reduces wasted effort; it does not guarantee a merge.

Small bug fixes, tests, doc corrections, and narrowly scoped improvements may
go straight to pull requests.

## Integration and attribution

Maintainers may edit, refactor, reorganize, squash, or partially incorporate
contributed work for consistency and maintainability.

Materially incorporated work is credited (commits, co-authorship, release notes,
acknowledgements, or contributor records). Attribution does not mean the code
stays unchanged or permanent.

## Decision authority

Maintainers decide merges into protected branches and official releases.

Repo access, commit access, or past accepted work does not confer architectural
authority. Main is curated, not crowdsourced.

Community feedback and evidence matter; final calls sit with maintainers who
support the result.

Subsystem maintainers may be delegated later; that does not remove project-wide
architectural and release authority.

## Forks and independent development

Open-source licenses allow independent experiments and forks under their terms.

Declining a contribution is about the maintained upstream, not a claim that the
idea has no merit elsewhere.

## Related documents

- [PROJECT_SCOPE.md](PROJECT_SCOPE.md) — mission boundaries and acceptance tests
- [CONTRIBUTING.md](CONTRIBUTING.md) — how to propose changes
- [profile/ARCHITECTURE.md](profile/ARCHITECTURE.md) — component ownership
- https://github.com/The-Iridium-Road/Steel — Steel (v0.1.0)
- [docs/operations/STEEL_V0_1_0_GATE.md](docs/operations/STEEL_V0_1_0_GATE.md) — historical Steel v0.1.0 ship criteria
