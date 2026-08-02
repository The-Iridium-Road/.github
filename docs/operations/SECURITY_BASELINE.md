# Security Baseline Checklist

Summary
Org security settings and vulnerability-reporting requirements for the live
bootstrap phase. This document alone changes nothing; it needs explicit approval
before execution.

## Organization

- [ ] 2FA required for organization members where the plan allows
- [ ] Owner count: sole owner initially; second trusted owner only when
      recovery and continuity actually need it
- [ ] Repository deletion restricted to owners
- [ ] Repository transfer restricted to owners
- [ ] Default member base permission: read (or lowest acceptable)
- [ ] Outside collaborators reviewed; avoid broad write by default
- [ ] Organization audit / security log reviewed periodically when available

## Vulnerability reporting

- [ ] Require GitHub private vulnerability reporting on every landed
      repository (core and otherwise). A repository is not considered landed
      until this is enabled.
- [ ] Do not publish a security email until a durable project/domain address
      exists
- [ ] `SECURITY.md` at org `.github` defaults remains accurate
- [ ] Public Issues are not used for vulnerability intake
- [ ] Discussions category Security (on `.github`) is process-only—never
      vulnerability intake

## While solo-maintainer

Do:

- [ ] Block force pushes to `main` on core repos once protections are applied
- [ ] Block deletion of the default branch
- [ ] Allow owner bypass for emergency recovery
- [ ] Prefer pull requests for meaningful architectural changes

Do not:

- [ ] Require a second reviewer while you are the only maintainer
- [ ] Invent bureaucracy that blocks emergency recovery
- [ ] Use Discussions as a substitute for private vulnerability reporting

## Branch protection / rulesets (later, per core repo)

When CI exists and live bootstrap is approved:

- [ ] Protect `main`: no force push, no branch deletion
- [ ] Require status checks once CI is real
- [ ] Owner bypass enabled for recovery
- [ ] Document any org-wide vs repo-level ruleset limits for the current GitHub plan

See also [REPOSITORY_MIGRATION.md](REPOSITORY_MIGRATION.md) for post-transfer
validation and [ORG_BOOTSTRAP.md](ORG_BOOTSTRAP.md) for ordered live steps.
