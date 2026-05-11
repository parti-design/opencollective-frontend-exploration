# Transformation

Back to: [Wiki Home](../Home.md)

This section tracks the longer-term effort to reshape Open Collective into something that fits the way funds, projects, and communities actually work in practice.

The intent is incremental and exploratory now, with an eventual horizon of forking the Open Collective codebase and adapting it. Until then, this is where we collect the friction, the patterns, and the structural ideas that come up while onboarding real users.

## What lives here

This section is organized in three layers, from observed to designed:

### [Pain Points](./pain-points/README.md) — what we observed

Concrete moments of confusion or friction observed while onboarding people or using the platform. Each is a small, dated entry with what was observed, where it happened, and the underlying issue it points to.

### [Patterns](./patterns/README.md) — how we think about it

Architectural and design-language patterns that surface across multiple pain points. These are the bigger structural ideas — how the product is organized, who it speaks to, where boundaries should be drawn.

### [Features](./features/README.md) — what we want to build

Designed solutions for the new version of Open Collective, specified in enough detail to inform implementation later. Features are where pain points and patterns turn into something buildable.

## How to use this section

- Drop new observations into `pain-points/` as they come up. Small, frequent, dated.
- When several pain points point at the same underlying issue, lift the structural insight into `patterns/` and link the pain points to it.
- When a pattern stabilizes into something you'd actually build, write it up under `features/` as a numbered spec (`FNNN-slug.md`).
- Use this section to shape the future transformation scope. It is not a bug tracker for upstream Open Collective.

## Relationship to [`docs/wiki/docks/`](../docks/Current-Focus.md)

The `docks/` section is the working journal for active exploration of Open Collective as it exists today — current focus, code-level architecture findings, branch-specific implementation notes (e.g. Swish on `swish-implementation`). It is shorter-lived and code-adjacent.

This `transformation/` section is the longer-horizon design spec for the new version. The two cross-reference each other: `docks/` findings about how OC works today feed into `features/` specs for the new version, and `features/` specs cite the prior `docks/` research instead of duplicating it.

## Current themes

- The platform serves two distinct audiences (funders and organizers) but presents one undifferentiated surface to both.
- Financial language on the platform conflates historical totals with operational availability.
- Many friction points appear when an organizer or fund manager is trying to do operational work but is surrounded by funder-facing framing.
- The shared-platform model collapses brand and operational control onto a single multi-tenant installation, even though almost no real features require it.
- Host-specific needs (regional payment providers, local integrations) are forced through a platform-wide release cycle because there is no extension model.
