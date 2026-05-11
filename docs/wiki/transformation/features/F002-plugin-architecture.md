# F002 — Plugin architecture

Back to: [Features](./README.md) | [Transformation](../README.md)

## Summary

A plugin architecture that lets host instances extend the platform without touching the core. Payment providers, regional integrations, language packs, sector-specific flows, and product-surface extensions should be installable per instance, the way WordPress plugins are installable per site.

## Why this exists

- Pain point: [002 — Fiscal host owns the relationship but not the platform](../pain-points/002-fiscal-host-brand-confusion.md) (the "host needs are forced into a monolithic release cycle" aspect)
- Pattern: [Host instance as first-class brand](../patterns/host-instance-as-first-class-brand.md)
- Prior research: [docks/Architecture and Constraints — Plugin Architecture Direction](../../docks/Architecture-and-Constraints.md), [docks/Ideas and Questions — Plugin Model](../../docks/Ideas-and-Questions.md), Swish implementation branch `swish-implementation`

The monolith forces a platform-wide release for any single host's need. Many host-specific needs (regional payment providers being the obvious one) have nothing to do with other hosts but currently require platform consensus to ship. F002 makes those needs solvable inside one instance.

## Shape of the solution

### Core / extension boundary

Adopt the principle already articulated in [docks/Architecture and Constraints](../../docks/Architecture-and-Constraints.md):

- **Core owns:** orders, transactions, expenses, payout methods, settlement state, permissions, audit trail. The ledger and trust model stay in core.
- **Extensions own:** provider configuration, capability state, provider-specific metadata, external references and event logs, surface-level UI for the things they add.

This boundary keeps the ledger safe while leaving room for plugins to do real work.

### Initial extension surfaces

Start with surfaces that have proven, concrete demand. From prior exploration:

- **Receiving money / contributor checkout** — regional payment providers (Swish, MobilePay, iDEAL, regional bank rails). The Swish work on `swish-implementation` is the prototype for this surface.
- **Payout / reimbursement methods** — regional rails for paying expenses.
- **Fundraising page enhancements** — campaign-style elements, goal widgets, sector-specific layouts.
- **Ticketing or event extensions** — event-shaped collectives with their own surface.

Surfaces should be added when there is real demand, not speculatively.

### Plugin shape

- A plugin is an installable bundle that registers into one or more defined extension surfaces.
- The plugin contract is declared, versioned, and capability-typed (a payment plugin declares it provides "checkout" capability, a payout plugin declares "payout" capability, etc.).
- Plugins are installed per instance. A host enables and configures the plugins they want; the rest of the platform is unaffected.
- Plugin authors can ship plugins independently of the core release cycle.

### Configuration and trust

- Plugins are configured at the host (instance) level, not at the collective level, for any plugin that touches money or compliance. Collective-level plugins may be allowed for purely cosmetic or workflow extensions.
- A plugin manifest declares the capabilities it claims, the data it reads and writes, and any external services it talks to. Hosts review the manifest before installing.
- The platform should ship a small set of audited first-party plugins so a fresh instance is useful out of the box.

### Out of scope for this feature

- A marketplace, billing for plugins, or plugin discovery UX. That is downstream.
- Sandboxing plugins to the level of running untrusted code. Initial plugins are trusted code installed by the host operator.
- Cross-instance plugin distribution standards.

## Open questions

Carried forward from [docks/Ideas and Questions — Plugin Model](../../docks/Ideas-and-Questions.md):

- Which extension surfaces are valuable enough to formalize first?
- Should plugins be defined through host settings or a dedicated installation model?
- How much of the plugin contract should live in GraphQL versus frontend configuration?
- What is the smallest convincing plugin (the "hello world payment provider")?
- How are plugin upgrades and breaking changes handled?
- What is the relationship between plugins and per-host theming from [F001](./F001-per-host-branding-and-instance.md)? (Probably: theming is a built-in concern; plugins are functional extensions.)

## Relationship to existing exploration

The plugin direction is already partially designed in [docks/Architecture and Constraints](../../docks/Architecture-and-Constraints.md) and prototyped in the `swish-implementation` branch (see [docks/Implementation Log](../../docks/Implementation-Log.md)). F002 lifts that exploration into a forward-looking spec for the new version and re-frames it from "an extension seam inside upstream Open Collective" to "the primary extensibility mechanism in a per-host-instance world."

When this feature gets built, the existing Swish work is the natural first concrete plugin.
