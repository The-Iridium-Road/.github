# Repository Migration Checklist

Summary
How repositories land under `The-Iridium-Road`: classify, invent licenses,
transfer or create, validate remotes. Transfers and creates are live actions and
need a separately approved phase. This file does not move anything by itself.

## Classification

Before migrating or creating a repository under the org, classify it:

```text
core — yes
tooling — yes
research — yes
experimental — yes (label maturity aggressively)
archived — only if historically relevant; label as Archived
unrelated — no
```

Do not migrate a repo merely because it once mentioned NPUs.

## Current repository inventory

```text
Carbon-XDNA — core — Developer Preview / v0.6.0
  Migrate first after .github

Steel — core / tooling — In development / pre-v0.1.0
  Create under org when STEEL_V0_1_0_GATE.md passes

Diamond-accel0 — core — Experimental / v0.0.5
  Migrate after Steel’s org landing (Carbon → Steel → Diamond)

NPUTOP — tooling — Planned / prototype
  Migrate only when presentable

Examples / utilities — tooling — Planned
  Category later; do not invent empty repos

Iron / Peano / MLIR-AIE — unrelated (external) — Upstream/reference
  Never present as Iridium Road repositories
```

## License gate (mandatory)

- [ ] Complete [LICENSE_AND_PROVENANCE.md](LICENSE_AND_PROVENANCE.md) inventory
      for the candidate repository before transfer or public create
- [ ] Especially for Steel: finish ancestry inventory as part of
      [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md)

## Landing order

1. `.github` (organization control plane — this repository)
2. Carbon-XDNA
3. Steel — when the [v0.1.0 gate](STEEL_V0_1_0_GATE.md) passes; create
   `The-Iridium-Road/Steel` directly under the organization when possible
   (prefer create over personal-account-then-transfer)
4. Diamond-accel0
5. NPUTOP or other observability projects (only if presentable)
6. Examples and utilities later
7. Research / specification repositories when warranted
8. Historical experiments worth preserving (Archived)
9. Everything else only after deliberate classification

Iron / Peano / MLIR-AIE: external only—never migrate or present as Iridium Road
repositories.

### Explicit non-goals for this documentation phase

Do not treat editing these checklists as authorization to:

- Perform live transfers or organization settings changes
- Start unrelated product work (runtime backends, major driver feature branches,
  observability redesigns, or new example workloads) as a side effect of org docs
- Build elaborate automation, project boards, or oversized team structure while
  the organization is still minimally staffed

## Per-repository transfer checklist

Before transfer:

- [ ] Classification recorded (core / tooling / research / experimental / archived)
- [ ] License/provenance inventory complete
- [ ] README has maturity status near the top
- [ ] Description and topics drafted (see [ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md))
- [ ] Confirm permissions on source account and destination organization
- [ ] Plan to enable private vulnerability reporting immediately on landing
      (required gate—repository is not landed until enabled)

After transfer:

- [ ] Verify remotes and fetch:

  ```bash
  git remote -v
  git fetch --all --prune
  git push --dry-run
  ```

- [ ] Update local origin explicitly, e.g.:

  ```bash
  git remote set-url origin \
    git@github.com:The-Iridium-Road/Carbon-XDNA.git
  ```

- [ ] Update documentation URLs, badges, submodules, package metadata,
      workflow references, and clone instructions (do not rely on redirects)
- [ ] Required: enable private vulnerability reporting (not landed until done)
- [ ] Confirm org default community health files apply or are overridden intentionally
- [ ] Apply branch protection when ready ([SECURITY_BASELINE.md](SECURITY_BASELINE.md))

## Steel create checklist (prefer over transfer)

When [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md) is complete:

- [ ] Create `The-Iridium-Road/Steel` under the organization
- [ ] Push history that has been scrubbed of secrets, junk, and giant artifacts
- [ ] Tag `v0.1.0` and publish release notes
- [ ] Set description, topics, and README status
- [ ] Required: enable private vulnerability reporting (not landed until done)
- [ ] Link from organization profile materials and pins when ready

## Suggested repository descriptions

Carbon-XDNA
Fedora-oriented AMD XDNA kernel driver stack providing robust NPU execution,
capability discovery, diagnostics, and observability.

Steel
Compile-only NPU artifact tooling for The Iridium Road: compile, optimize, and
construct executable NPU artifacts for Diamond and other consumers.

Diamond-accel0
Userspace AMD NPU runtime and execution platform, directly downstream of
Carbon-XDNA and Fedora's XDNA driver stack. Diamond is not a kernel driver.

## Post-stack pins

After repositories exist and are presentable, follow pin order in
[ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md). Pins are a live action; do not apply them
as a side effect of editing this checklist.
