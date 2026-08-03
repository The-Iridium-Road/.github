# Steel v0.1.0 Release Gate (historical)

Summary
Ship criteria that defined the first public Steel release. v0.1.0 is published
at https://github.com/The-Iridium-Road/Steel. This document is kept as the
record of what “done enough to ship” meant—not as an open blocker list.

Further work belongs in v0.1.1 or v0.2.0.

## Outcome

- Repository: https://github.com/The-Iridium-Road/Steel
- Tag: v0.1.0
- Role: compile-only library for Diamond-accel0; derived from upstream Iron with
  heavy modification for that runtime

## Gate checklist (criteria that defined v0.1.0)

- [x] Clean production build from a fresh checkout
- [x] Public headers are self-contained
- [x] `steel_forge_request_t` extensibility decision resolved
- [x] Failure diagnostics remain retrievable
- [x] Compiler subprocess timeout and cleanup behavior defined
- [x] Vector-add smoke passes cold and warm
- [x] Failure-injection tests pass
- [x] No device access or XRT linkage in the production library
- [x] Dependency and inherited-code licenses inventoried
      (see Steel LICENSE, NOTICE, ACKNOWLEDGEMENTS, steel/LICENSE_INVENTORY.md
      and [LICENSE_AND_PROVENANCE.md](LICENSE_AND_PROVENANCE.md))
- [x] Installation and minimal-use instructions work
- [x] Known limitations are documented
- [x] Version reports `0.1.0`
- [x] Repository history contains no secrets, generated junk, or giant artifacts
- [x] Tag and release notes prepared

## Landed verification (maintainers)

Confirm after publish (live org actions—not implied by editing this file):

- [ ] Org profile and root README link Steel correctly
- [ ] Private vulnerability reporting enabled on The-Iridium-Road/Steel
- [ ] Pins updated when ready ([ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md))
