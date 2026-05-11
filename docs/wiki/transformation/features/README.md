# Features

Back to: [Transformation](../README.md) | [Wiki Home](../../Home.md)

This is where pain points and patterns become specs. A feature page describes a designed solution for the new version of Open Collective in enough detail to inform implementation later.

A feature usually earns a page when:

- one or more pain points point at a concrete missing capability, and
- a pattern has been identified that frames the solution direction, and
- the shape of the solution is stable enough to start specifying.

Features may stay open-ended for a while. The point is to have one place where the "thing we want to build" is captured, separate from the "thing we observed" (pain points) and the "way of thinking about it" (patterns).

## Entry format

Each feature is its own file, prefixed with an ID:

- `FNNN-short-slug.md`
- short summary of what the feature is
- why it exists (pain points and patterns it answers)
- shape of the solution at the current level of detail
- open questions and unknowns
- relationship to existing exploration in [`docs/wiki/docks/`](../../docks/Architecture-and-Constraints.md) if the feature has prior research

## Index

- [F001 — Per-host branding and instance](./F001-per-host-branding-and-instance.md) — each fiscal host runs their own branded instance, like a WordPress site
- [F002 — Plugin architecture](./F002-plugin-architecture.md) — host-installable extensions for payment providers, regional integrations, and product surfaces
