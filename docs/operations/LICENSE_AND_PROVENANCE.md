# License and Provenance Policy

Summary
There is no universal default license for The Iridium Road. Kernel-derived code
and original userspace libraries have different constraints. Inventory licenses
before every transfer or public create.

## Policy by category

```text
Organization .github control-plane repo — Apache-2.0 (see root LICENSE)

Carbon / kernel-oriented code — preserve applicable Linux/kernel licensing;
  generally GPL-2.0-only for kernel modules and kernel-derived material

Original userspace (e.g. Diamond, Steel as original work) — prefer Apache-2.0
  for new original code (explicit patent grant)

Documentation — keep under the repository license initially; split to CC BY 4.0
  only if that split is genuinely useful

Third-party and inherited code — retain upstream licenses and attribution;
  do not relicense incompatible material
```

The `.github` repository license does not change Carbon/kernel GPL obligations
or third-party terms in other repositories.

Existing third-party and inherited code must keep compatible licensing.
Apache-2.0 for new userspace work does not override obligations for vendored or
forked trees.

## Mandatory inventory gate (before every transfer)

Complete this checklist for each repository before transferring it into
`The-Iridium-Road`:

- [ ] Top-level `LICENSE` (or equivalent) identified
- [ ] List of bundled/vendored third-party trees and their licenses
- [ ] List of files or directories under different terms than the top-level license
- [ ] SPDX or documented license identifiers recorded for major components
- [ ] Patent/notice files retained where required (e.g. NOTICE for Apache-2.0 trees)
- [ ] README states license summary and points to full texts
- [ ] No claim that The Iridium Road “owns” external upstream projects (Iron,
      Peano, MLIR-AIE, vendor firmware, etc.)

Do not transfer until unresolved provenance questions are written down.

## Steel toolchain ancestry

Steel inherits a toolchain ancestry worth documenting carefully before any
public organization repository exists. License inventory is a required item on
the [v0.1.0 gate](STEEL_V0_1_0_GATE.md).

- [ ] Document which Iron / Peano / MLIR-AIE (or other) components influenced or
      were incorporated into Steel
- [ ] Separate original Iridium Road code from upstream-derived code
- [ ] Record licenses for each incorporated component
- [ ] Confirm the public Steel license story is accurate when
      [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md) is closed
- [ ] Ensure organization materials describe Steel as Iridium Road artifact
      tooling without implying ownership of AMD/upstream projects

## Pull requests touching provenance

Contributors and maintainers should note license/provenance impact in the PR
template when adding or modifying vendored or upstream-derived code.
