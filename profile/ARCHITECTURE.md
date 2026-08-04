# Architecture

Summary
Ownership map for Carbon, Diamond, and Steel. Read this before proposing
cross-component changes. Runtime diagram and organization landing order are
both here.

## Stack

Runtime and dependency relationships (not organization landing order):

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

Landing order: `.github` → Carbon-XDNA → Steel (landed at v0.1.3) →
Diamond-accel0 → NPUTOP → examples. See
[REPOSITORY_MIGRATION.md](../docs/operations/REPOSITORY_MIGRATION.md).

## Naming

The name is intentional: upstream Iron, refined for a stack that already has
Carbon, becomes Steel—the compile-only layer Diamond consumes. Deliberate
metallurgy, not decoration.

## Ownership

Carbon-XDNA
Owns: kernel integration, execution transport, capability discovery,
diagnostics, observability, fault containment at the driver boundary.
Does not own: compilation, userspace scheduling, application policy.

Diamond-accel0
Owns: program lifecycle, scheduling, artifact selection, compile
orchestration, caching/policy, loading, dispatch.
Does not own: kernel hardware management; low-level artifact production.

Steel
Owns: compiling, optimizing, and constructing executable NPU artifacts.
Does not own: runtime scheduling, NPU dispatch, kernel interfaces.
Does not open the NPU or link XRT in the production library.

Repository: https://github.com/The-Iridium-Road/Steel

NPUTOP / tools
Owns: inspection, diagnostics, telemetry, compatibility checks.
Does not own: execution policy or compilation.

### Steel status and provenance

Current tip: Experimental v0.1.3
(https://github.com/The-Iridium-Road/Steel/releases/tag/v0.1.3).
Paired toolchain Release: toolchain-v2026.08.2 (unchanged for v0.1.3; no new
forge-bag Release). Product tags and toolchain tags are independent; consumers
pair via `steel/toolchain.lock`.

Steel remains compile-only artifact production for Diamond-accel0: no NPU open,
no XRT in the production library. Integrator contract since the 0.1 line: pinned
toolchain Release (since v0.1.1); forge-owned FULL packager via hrx `xclbinutil`
inside the lit bag—not host `/opt/xilinx/xrt` (since v0.1.2); embed-safe CMake
(`CMAKE_CURRENT_SOURCE_DIR`) so Diamond can `add_subdirectory` without path
hacks (since v0.1.2); additive `steel_io_abi/1` native-join prepare keys on
successful forge so Diamond can prepare the join pin without parsing MLIR or
Bootstrapping opcode (since v0.1.3). Public ABI shapes since v0.1.0 are
unchanged; version macros track the product tip (0.1.3). Depth: Steel README,
STEEL_API.md, NATIVE_JOIN_PHASE.md, forge README, ACKNOWLEDGEMENTS, and
releases—not duplicated here.

The historical ship criteria that defined the first public tag (v0.1.0) are
recorded in [STEEL_V0_1_0_GATE.md](../docs/operations/STEEL_V0_1_0_GATE.md).
Release line summary:
[RELEASE_CONVENTIONS.md](../docs/operations/RELEASE_CONVENTIONS.md).

Steel is derived from upstream Iron and has been heavily modified, optimized,
and re-architected for Diamond-accel0. Upstream Iron remains external; Iridium
Road does not claim ownership of Iron, Peano, or MLIR-AIE. Credit and lineage
detail live in Steel’s ACKNOWLEDGEMENTS.md.

### Diamond and compilation

Diamond owns compilation orchestration: when to compile, which artifacts to
select or cache, how results enter execution. Steel owns artifact production.
Do not describe Diamond as the compiler itself.

Status: In development v0.0.5 — working native XDNA userspace runtime with
program/product store, optional Steel compile-to-product, and hardware-proven
scale execution. Phases 1–5 complete; Phase 6 (Steel→native join and reference
CLI) in progress toward a later v0.1.0 product line. Not landed under the org
yet.

Diamond consumes Steel products/forge results; prepare-program joins products
to native exec. Today’s production path is native DRM/amdxdna (XRT oracle-only).
The Carbon-enhanced path is deferred for now. The stack diagram above remains
the intended long-term ownership map—not a claim that Carbon is required for
current Diamond hardware proves.

## External tooling (not Iridium Road)

Upstream or provenance references only:

- Iron — upstream compiler lineage that Steel derives from (heavily modified
  for Diamond-accel0; not an Iridium Road product)
- Peano
- MLIR-AIE

Do not present these as organization repositories.

## Maturity vocabulary

Use consistently in READMEs and org materials:

`Experimental` · `Developer Preview` · `Beta` · `Stable` · `Archived` ·
`Planned` · `In development`

“Public repository” and “safe to install” are not the same. Put status near the
top of every repository README.

## Scope and governance

Boundaries above support a workload-neutral platform. AI/ML and other domains
may consume the stack; they must not redefine it. Contributions are proposals.
See [PROJECT_SCOPE.md](../PROJECT_SCOPE.md) and [GOVERNANCE.md](../GOVERNANCE.md).
