# Project Scope

Summary
What The Iridium Road is trying to become, and what must not steer it. Use this
when judging whether a feature or subsystem belongs upstream.

## In scope

- A Linux-native stack for compiling, executing, observing, and recovering
  arbitrary supported NPU programs on AMD XDNA-class hardware (initially Fedora).
- Workload-neutral infrastructure: Carbon (kernel), Diamond (runtime /
  orchestration), Steel (artifact production), and supporting tools.
- Applications and examples that exercise the general model—including AI/ML,
  media, scientific, or other domains—as consumers of the platform.
- Correctness, recoverability, observability, compatibility, and measurable
  performance of that general model.

## Out of scope (as governing goals)

- Steering the core architecture around one workload category (including AI/ML
  inference, training, or media effects).
- Becoming a vendor demo stack or webcam-effects showcase.
- Accepting features mainly because they are popular rather than because they
  fit general-purpose NPU programmability.
- Expanding faster than maintainers can test, support, and recover on available
  hardware.

AI and machine learning workloads are allowed. They are not privileged. They do
not define component boundaries, public APIs, scheduling policy, or roadmap
priority for the core stack.

## Acceptance tests for proposed changes

A feature or subsystem should generally satisfy:

1. Does it support general-purpose NPU programmability?
2. Does it preserve the component boundaries
   ([profile/ARCHITECTURE.md](profile/ARCHITECTURE.md))?
3. Does it improve correctness, portability, observability, performance, or
   usability of the general platform?
4. Does its maintenance burden justify its value?
5. Does it avoid privileging one workload category in the core design?
6. Can it be tested and supported with available hardware and maintainer
   capacity?

Scope outranks popularity. See [GOVERNANCE.md](GOVERNANCE.md) for who decides.
