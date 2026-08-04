# The Iridium Road

Summary
Organization profile for The Iridium Road—what it is, what exists today, and
where to go next. General-purpose NPU computing for Linux. Not an AI-first
project. Not a webcam-effects demo stack.

The full control-plane map (directory of this `.github` repository, document
guide, landing order) lives in the repository root [README.md](../README.md).

## Mission

Building a Linux-native stack for compiling, executing, observing, and
recovering arbitrary supported programs on AMD NPUs.

On-die compute often sits behind incomplete drivers, fragmented vendor tooling,
and heavyweight compiler stacks. This project aims to make that hardware
programmable and usable through a coherent Linux stack.

The aim—not a claim of completion today—is that end users can find useful NPU
software for Linux, and developers can find docs, examples, tooling, and
reliable interfaces instead of disconnected experiments.

The infrastructure is workload-neutral. AI and machine learning may use the
platform; they do not steer its architecture. Details:
[PROJECT_SCOPE.md](../PROJECT_SCOPE.md).

## Project stack

Landing order (runtime relationships are in [ARCHITECTURE.md](ARCHITECTURE.md)):

- Carbon-XDNA — Fedora-oriented AMD XDNA kernel driver stack (device lifecycle,
  capability discovery, execution transport, diagnostics, observability, fault
  containment). Maturity: see Current status.
- Steel — Compile-only tooling to compile, optimize, and construct executable
  NPU artifacts. Public at https://github.com/The-Iridium-Road/Steel (v0.1.3).
  Derived from upstream Iron; heavily modified for Diamond-accel0. The name is
  intentional: Iron + Carbon → Steel. Integrator notes (toolchain pin, forge
  FULL packager, CMake embed, native-join `io_abi`): root
  [README.md](../README.md) and [ARCHITECTURE.md](ARCHITECTURE.md).
- Diamond-accel0 — In development v0.0.5: working native XDNA userspace runtime
  with program/product store, optional Steel compile-to-product, and
  hardware-proven scale execution; source→Steel→verified NPU join and the
  reference CLI are active Phase 6 work. Not a v0.1.0 product yet. Not a kernel
  driver; does not own artifact production (Steel does). Details:
  [ARCHITECTURE.md](ARCHITECTURE.md).
- Observability and utilities — Planned supporting work: monitoring, diagnostics,
  profiling, compatibility checks, reference workloads, and practical NPU
  applications.

Issues and pull requests are proposals, not merge obligations. See
[GOVERNANCE.md](../GOVERNANCE.md) and [CONTRIBUTING.md](../CONTRIBUTING.md).

## Current status

```text
Carbon-XDNA — Developer Preview, v0.6.0 (current focus of active use)
Steel — Experimental, v0.1.3 — https://github.com/The-Iridium-Road/Steel
Diamond-accel0 — In development, v0.0.5 — native XDNA userspace; Phase 6 join/CLI in progress; not a v0.1.0 product yet
NPUTOP — Planned; prototype exists elsewhere, not presented as org-ready yet
Examples / utilities — Planned category, not a published repo yet
```

Versions and maturity can change; treat each repository README as authoritative.
Focus today: AMD XDNA NPUs on Fedora.

## Repository map

```text
Carbon-XDNA — Fedora-oriented AMD XDNA kernel driver stack
Steel — Compilation and executable artifact construction
        https://github.com/The-Iridium-Road/Steel
Diamond-accel0 — Userspace runtime aimed at arbitrary supported NPU execution
NPU observability tools — Monitoring, diagnostics, profiling, inspection (planned)
Examples and utilities — Reference workloads and practical applications (planned)
Specifications and research — Decisions, measurements, compatibility data (as needed)
```

Iron, Peano, and MLIR-AIE are external upstream/reference tooling—not Iridium
Road repositories. Steel’s Iron lineage and credits are documented in Steel’s
ACKNOWLEDGEMENTS.md.

## Reporting issues and security

- Bugs and support: open an Issue on the relevant repository.
  [SUPPORT.md](../SUPPORT.md)
- Security: GitHub private vulnerability reporting on the affected repository.
  [SECURITY.md](../SECURITY.md)

## Principles

- The hardware belongs to the user. Owner-programmable on-die compute, not
  limited to vendor-endorsed workloads.
- Arbitrary supported execution is foundational. Inference and media effects may
  be supported; they are not the boundary.
- Workload neutrality. No single category—including AI—governs the core design.
- Linux first. Initial platform: Fedora and its AMD XDNA kernel stack.
- Failure must be contained. App mistakes should not take down device, driver,
  or OS where isolation is possible.
- Performance must be measurable. Evidence over claims; document hardware and
  firmware limits.
- Useful software is the long-term destination. Drivers and runtimes are
  infrastructure toward a Linux NPU application ecosystem—not a claim that the
  ecosystem already exists.

## License

This organization `.github` repository is under the
[Apache License 2.0](../LICENSE).
