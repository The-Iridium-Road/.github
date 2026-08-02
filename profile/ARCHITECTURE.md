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

Landing order: `.github` → Carbon-XDNA → Steel (at v0.1.0) → Diamond-accel0 →
NPUTOP → examples. See
[REPOSITORY_MIGRATION.md](../docs/operations/REPOSITORY_MIGRATION.md).

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

NPUTOP / tools
Owns: inspection, diagnostics, telemetry, compatibility checks.
Does not own: execution policy or compilation.

### Steel publish gate

Steel is a public component: compile-only NPU artifact tooling prepared for
Diamond integration. Independent component; expected to be part of or consumed
by Diamond.

Until the [v0.1.0 gate](../docs/operations/STEEL_V0_1_0_GATE.md) passes:

- Keep Steel on maps without an organization repository URL.
- The gate is the ship criteria—not unbounded polishing.

When the gate passes:

- Publish `The-Iridium-Road/Steel` under the org (prefer create over
  personal-repo-then-transfer).
- Tag v0.1.0 only after the gate checklist passes; further polish is v0.1.1 or
  v0.2.0.

### Diamond and compilation

Diamond owns compilation orchestration: when to compile, which artifacts to
select or cache, how results enter execution. Steel owns artifact production.
Do not describe Diamond as the compiler itself.

## External tooling (not Iridium Road)

Upstream or provenance references only:

- Iron — AMD/related compiler tooling
- Peano
- MLIR-AIE

Not Iridium Road products; do not present them as organization repositories.

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
