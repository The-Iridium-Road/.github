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

Original userspace (e.g. Diamond; new Steel code) — prefer Apache-2.0 for new
  original code (explicit patent grant); retain upstream terms for Iron-derived
  or other inherited material in Steel

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

Steel product tip is Experimental v0.1.2 at
https://github.com/The-Iridium-Road/Steel. It is derived from upstream Iron and
has been heavily modified, optimized, and re-architected for Diamond-accel0.
Upstream Iron is not an Iridium Road product.

Primary inventory lives in the Steel repository:

- LICENSE, NOTICE
- ACKNOWLEDGEMENTS.md (Iron origin, credit)
- steel/LICENSE_INVENTORY.md
- LEGAL/ (including hrx KEEP for the forge FULL packager)

Toolchain Releases carry scrubbed LEGAL / notices. The FULL packager KEEP
component is documented in Steel `LEGAL/` (hrx). System XRT is not redistributed
and is not a supported packager. Do not paste full LEGAL tables into this
control plane.

Org materials should describe Steel as Iridium Road compile-only artifact
tooling without claiming ownership of Iron, Peano, or MLIR-AIE. Historical first
ship criteria: [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md). Release line:
[RELEASE_CONVENTIONS.md](RELEASE_CONVENTIONS.md).

Maintainer checks (keep current as Steel evolves):

- [ ] Steel ACKNOWLEDGEMENTS and LICENSE_INVENTORY stay accurate after merges
- [ ] Org profile / architecture wording still matches Steel’s public story
- [ ] No implication that Iridium Road owns upstream Iron

## Pull requests touching provenance

Contributors and maintainers should note license/provenance impact in the PR
template when adding or modifying vendored or upstream-derived code.
