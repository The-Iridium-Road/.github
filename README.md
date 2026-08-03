# The Iridium Road

Summary
Front door for the organization control plane (`The-Iridium-Road/.github`).
Mission, current status, stack map, and a directory of every public file in this
repository. This is not a claim that the full stack is finished—it is the
charter and the map.

General-purpose NPU computing for Linux. Not an AI-first project. Not a
webcam-effects demo stack.

## Mission

The Iridium Road is building a Linux-native stack for compiling, executing,
observing, and recovering arbitrary supported programs on AMD NPUs.

Modern processors ship with on-die compute that Linux users often cannot freely
program without incomplete drivers, fragmented vendor tooling, undocumented
interfaces, and heavyweight compiler stacks. This project exists to change that.

The aim—not a claim of completion today—is:

- End users searching for “NPU programs Linux” can find installable, useful
  software that makes real use of hardware already in the machine.
- Developers searching for “NPU programming Linux” can find documentation,
  examples, tooling, diagnostics, and reliable execution interfaces—not a pile
  of disconnected experiments.

The platform is workload-neutral. AI and machine learning may use it; they do
not define or steer the architecture. See [PROJECT_SCOPE.md](PROJECT_SCOPE.md).

## Project stack

Intended organization landing order (runtime relationships:
[profile/ARCHITECTURE.md](profile/ARCHITECTURE.md)):

```text
Carbon-XDNA
  Fedora-oriented AMD XDNA kernel driver stack
  lifecycle · transport · capabilities · diagnostics · observability

Steel
  Compile-only tooling: compile, optimize, construct executable NPU artifacts
  Public at https://github.com/The-Iridium-Road/Steel (v0.1.2)
  Derived from upstream Iron; heavily changed for Diamond-accel0

Diamond-accel0
  Userspace runtime in heavy development; not release-ready (v0.0.3)
  lifecycle · scheduling · orchestration · dispatch · APIs
  Not a kernel driver; does not own artifact production

Observability and utilities (planned)
  monitoring · diagnostics · profiling · examples · practical applications
```

The name is intentional: upstream Iron, refined for a stack that already has
Carbon, becomes Steel—the compile-only layer Diamond consumes.

### Steel for integrators (since v0.1.0)

Current tip: Experimental v0.1.2
(https://github.com/The-Iridium-Road/Steel/releases/tag/v0.1.2).
Paired toolchain Release: toolchain-v2026.08.2
(https://github.com/The-Iridium-Road/Steel/releases/tag/toolchain-v2026.08.2).
Product tags and toolchain tags are independent; pair via `steel/toolchain.lock`.

- Still compile-only `libsteel_bridge` / `steel_forge`: no NPU open; production
  link line stays free of XRT/device libs.
- Since v0.1.1: pinned toolchain Release via `steel/toolchain.lock` and
  `light_steel_forge.sh` (not a hand-copied Iron tree).
- Since v0.1.2: FULL packaging uses forge hrx `xclbinutil` inside the lit
  bag—not host `/opt/xilinx/xrt`. INSTS unchanged.
- Since v0.1.2: CMake is embed-safe (`CMAKE_CURRENT_SOURCE_DIR`); Diamond can
  `add_subdirectory` Steel without rewriting Steel’s source-root paths.
- Depth: Steel README, `steel/STEEL_API.md`, `forge/README.md`, and releases.
  Ownership and contract summary:
  [profile/ARCHITECTURE.md](profile/ARCHITECTURE.md).

```text
Applications / utilities
        │
        ▼
     Diamond
 runtime · scheduling · lifecycle · dispatch · compile orchestration
        │
        ├──────────────► Steel
        │     compile · optimize · construct executable artifacts
        ▼
   Carbon-XDNA
 kernel interfaces · transport · capabilities · observability
        │
        ▼
 AMD XDNA hardware / firmware
```

Iron, Peano, and MLIR-AIE remain external upstream/reference tooling. They are
not Iridium Road repositories. See [profile/ARCHITECTURE.md](profile/ARCHITECTURE.md)
and Steel’s ACKNOWLEDGEMENTS for provenance.

## Current status

```text
Carbon-XDNA — Developer Preview, v0.6.0 (current focus of active use)
Steel — Experimental, v0.1.2 — https://github.com/The-Iridium-Road/Steel
Diamond-accel0 — In development, v0.0.3 — heavy development; not release-ready
NPUTOP — Planned; prototype exists elsewhere, not presented as org-ready yet
Examples / utilities — Planned category, not a published repo yet
```

Versions and maturity change. Treat each component repository’s README as
authoritative. Focus today: AMD XDNA-class NPUs on Fedora Linux.

## Principles

- The hardware belongs to the user.
- Arbitrary supported execution is foundational; vendor-endorsed workloads are
  not the boundary.
- Workload neutrality: no single category, including AI, governs the core design.
- Linux first (Fedora and its AMD XDNA kernel stack initially).
- Failure must be contained where hardware and firmware allow.
- Performance must be measurable; limits should be documented, not hidden.
- Useful software is the long-term destination; drivers and runtimes are
  infrastructure toward that, not proof that the ecosystem already exists.

## How this organization is run

- Maintainer-led, contribution-friendly: issues and pull requests are proposals,
  not merge obligations. [GOVERNANCE.md](GOVERNANCE.md)
- Scope outranks popularity. [PROJECT_SCOPE.md](PROJECT_SCOPE.md)
- How to propose work, design-issue gate, DCO: [CONTRIBUTING.md](CONTRIBUTING.md)
- Bugs and help: Issues on the owning repository. [SUPPORT.md](SUPPORT.md)
- Security: private vulnerability reporting on the affected repository—not
  public Issues. [SECURITY.md](SECURITY.md)
- Conduct: [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)

## Repository directory

What lives in this `.github` control-plane repository:

```text
.
├── README.md                 This file — mission, status, and map
├── LICENSE                   Apache-2.0 for this repository
├── profile/
│   ├── README.md             Organization profile (shown on the org home page)
│   └── ARCHITECTURE.md       Ownership boundaries and stack diagram
├── PROJECT_SCOPE.md          In / out of scope; acceptance tests
├── GOVERNANCE.md             Who decides; contributions as proposals
├── CONTRIBUTING.md           How to contribute; DCO; design gates
├── SECURITY.md               Vulnerability and private conduct reporting
├── SUPPORT.md                Where to ask for help
├── CODE_OF_CONDUCT.md        Contributor Covenant 2.1
├── pull_request_template.md  Default PR checklist
├── .github/
│   └── ISSUE_TEMPLATE/       Org-default issue forms and contact links
│       ├── config.yml
│       ├── bug_report.yml
│       └── feature_request.yml
└── docs/
    └── operations/           Maintainer checklists (not live actions by themselves)
        ├── ORG_BOOTSTRAP.md
        ├── SECURITY_BASELINE.md
        ├── REPOSITORY_MIGRATION.md
        ├── LICENSE_AND_PROVENANCE.md
        ├── RELEASE_CONVENTIONS.md
        └── STEEL_V0_1_0_GATE.md   Historical v0.1.0 ship criteria
```

## Document guide

Start here if you want…

- What the project is → this file, then [profile/README.md](profile/README.md)
- Who owns which layer → [profile/ARCHITECTURE.md](profile/ARCHITECTURE.md)
- Whether a feature belongs → [PROJECT_SCOPE.md](PROJECT_SCOPE.md)
- Whether a PR is owed a merge → [GOVERNANCE.md](GOVERNANCE.md)
- How to send a change → [CONTRIBUTING.md](CONTRIBUTING.md)
- How to report a vulnerability → [SECURITY.md](SECURITY.md)
- Steel repository → https://github.com/The-Iridium-Road/Steel
- Steel release line → [docs/operations/RELEASE_CONVENTIONS.md](docs/operations/RELEASE_CONVENTIONS.md)
- Historical Steel v0.1.0 ship criteria → [docs/operations/STEEL_V0_1_0_GATE.md](docs/operations/STEEL_V0_1_0_GATE.md)
- How repos land under the org → [docs/operations/REPOSITORY_MIGRATION.md](docs/operations/REPOSITORY_MIGRATION.md)

## Intended landing order

```text
1. .github          (this repository)
2. Carbon-XDNA
3. Steel            (landed — v0.1.2 at The-Iridium-Road/Steel)
4. Diamond-accel0
5. NPUTOP           (when presentable)
6. Examples         (later)
```

Editing checklists in `docs/operations/` does not transfer repositories or change
org settings by itself.

## License

This repository is licensed under the [Apache License 2.0](LICENSE). Other
Iridium Road components may use different licenses (for example kernel-oriented
work). See [docs/operations/LICENSE_AND_PROVENANCE.md](docs/operations/LICENSE_AND_PROVENANCE.md).
