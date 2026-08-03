# Organization Bootstrap Checklist

Summary
Maintainer checklist for a separately approved live bootstrap phase. Editing
this file does not change GitHub settings, transfer repos, apply pins, or create
rulesets. Review docs first, then explicitly approve before doing anything live.

## Organization identity

- [ ] Confirm organization slug: `The-Iridium-Road`
- [ ] Set organization short description:

  > Building a Linux-native stack for compiling, executing, observing, and recovering arbitrary supported programs on AMD NPUs.

- [ ] Confirm organization is public as intended
- [ ] Ensure the `.github` repository exists, is public, and contains
      `profile/README.md` (organization profile)

## Security and access (live — after approval)

Follow [SECURITY_BASELINE.md](SECURITY_BASELINE.md) in full:

- [ ] Require two-factor authentication for the organization where available
- [ ] Keep a single owner initially; preserve account recovery path
- [ ] Restrict repository deletion and transfer to organization owners
- [ ] Set default member permission to least privilege tolerable
- [ ] Do not add a second owner merely to populate the settings page

## Teams (minimal)

Create teams even with few people so access can target teams later. Do not
invent elaborate team or project-board structure while staffing is minimal.

- [ ] `maintainers`
- [ ] `contributors`
- [ ] `security`

## Repository landing sequence

See [REPOSITORY_MIGRATION.md](REPOSITORY_MIGRATION.md):

1. `.github`
2. Carbon-XDNA
3. Steel (landed — https://github.com/The-Iridium-Road/Steel v0.1.2;
   first-ship criteria: [STEEL_V0_1_0_GATE.md](STEEL_V0_1_0_GATE.md))
4. Diamond-accel0
5. NPUTOP when presentable
6. Examples / utilities later

Landing prerequisite: every repository must have private vulnerability
reporting enabled before it is treated as landed. See
[SECURITY_BASELINE.md](SECURITY_BASELINE.md).

## Repository topics and descriptions (when repos land)

Carbon-XDNA
Fedora-oriented AMD XDNA kernel driver stack providing robust NPU execution,
capability discovery, diagnostics, and observability.

Steel
The Iridium Road’s low-latency compiler subsystem, producing executable AMD
XDNA NPU artifacts for the Diamond runtime.

Diamond-accel0
Userspace AMD NPU runtime and execution platform, directly downstream of
Carbon-XDNA and Fedora's XDNA driver stack. Diamond is not a kernel driver.

- [ ] Apply topics relevant to each repo (e.g. `amd`, `npu`, `xdna`, `fedora`,
      `linux`) without implying ownership of external upstream projects

## Pin order (eventual — max six public pins)

Apply only after the corresponding repositories exist and are presentable:

1. Carbon-XDNA
2. Steel (pin-eligible at v0.1.2)
3. Diamond-accel0
4. NPUTOP (when ready)
5. Documentation / architecture surface
6. Examples / demonstration repository (when it exists)

If the sixth slot is needed earlier for a hardware/compatibility matrix, swap
with examples only when that matrix repository actually exists.

- [ ] Pins applied in landing / story order
- [ ] Do not pin nonexistent or unpresentable repositories

## Explicitly out of scope for documentation work

Do not treat creation of this file as authorization to:

- Change organization settings
- Transfer or delete repositories
- Apply branch protections, rulesets, or pins
- Start unrelated product work (runtime backends, major driver feature branches,
  observability redesigns, or new example workloads) as a side effect of org
  documentation
