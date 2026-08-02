# Steel v0.1.0 Release Gate

Summary
Finite ship criteria for publishing `The-Iridium-Road/Steel`. Exists so
“polishing” does not become an infinite verb. Prefer creating the repo under the
org rather than personal-account-then-transfer.

Steel is a public component name before this gate passes; the organization
repository URL and v0.1.0 tag wait until every item below is checked.

## Gate checklist

- [ ] Clean production build from a fresh checkout
- [ ] Public headers are self-contained
- [ ] `steel_forge_request_t` extensibility decision resolved
- [ ] Failure diagnostics remain retrievable
- [ ] Compiler subprocess timeout and cleanup behavior defined
- [ ] Vector-add smoke passes cold and warm
- [ ] Failure-injection tests pass
- [ ] No device access or XRT linkage in the production library
- [ ] Dependency and inherited-code licenses inventoried
      (see [LICENSE_AND_PROVENANCE.md](LICENSE_AND_PROVENANCE.md))
- [ ] Installation and minimal-use instructions work
- [ ] Known limitations are documented
- [ ] Version reports `0.1.0`
- [ ] Repository history contains no secrets, generated junk, or giant artifacts
- [ ] Tag and release notes prepared

## Ship rule

Once every item passes: ship it.

Anything else becomes v0.1.1 or v0.2.0. Steel does not need to emerge as an
ABI-complete civilization.

After ship (required to consider the repository landed):

- [ ] Create `The-Iridium-Road/Steel` under the organization when possible
- [ ] Publish tag `v0.1.0` and release notes
- [ ] Link Steel from [profile/README.md](../../profile/README.md) and pins per
      [ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md)
- [ ] Required: enable private vulnerability reporting on the repository
      (Steel is not landed until this is on)

This document does not create the repository or cut the release by itself.
Live publish requires an explicit maintainer decision after the checklist is
complete.
