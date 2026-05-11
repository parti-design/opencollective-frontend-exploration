# F001 — Per-host branding and instance

Back to: [Features](./README.md) | [Transformation](../README.md)

## Summary

Each fiscal host runs their own instance of the platform, branded as their own platform. The Open Collective software becomes the engine; the host becomes the visible brand. Conceptually identical to WordPress: software that anyone installs, where each installation is its own named site.

## Why this exists

- Pain point: [002 — Fiscal host owns the relationship but not the platform](../pain-points/002-fiscal-host-brand-confusion.md)
- Pattern: [Host instance as first-class brand](../patterns/host-instance-as-first-class-brand.md)

Hosts carry the operational, legal, and support load for their collectives but do not control the brand contributors see or the platform behavior they support. Three brands appear in every donation flow (collective, host, Open Collective). The shared-platform model imposes these costs without delivering meaningful cross-host benefits in return.

## Shape of the solution

### Deployment model

- One installation per fiscal host. The host operates their own instance (self-hosted or managed).
- The platform is distributed as installable software. Upgrades, configuration, and operational ownership belong to the host.
- A managed-hosting option should exist for hosts who do not want to run servers themselves. The managed offering should not undermine the per-host brand model — each managed instance is still distinctly the host's.

### Brand surface

- Host names the platform. The application title, navigation chrome, transactional emails, receipts, and bank descriptors all carry the host's name.
- Host configures look and feel: logo, color, typography, imagery, possibly layout templates.
- Open Collective (the upstream software) is credited but not foregrounded — closer to a "powered by" footer than a co-brand.

### Identity boundaries

- Each instance is its own product surface. A contributor giving to a collective on Host A's instance is a contributor on Host A, not a contributor on Open Collective.
- Collectives belong to one host instance at a time. Cross-host coordination, if it ever exists, happens through opt-in federation, not shared identity.

### Out of scope for this feature

- Federation protocols for cross-host features. These are a separate spec if and when concrete cross-host needs emerge.
- Multi-host single-sign-on for contributors. May come later as a federation extension.
- Migrating existing Open Collective hosts onto independent instances. Migration tooling is its own spec.

## Open questions

- What is the minimum viable hosting story? Self-hosted only, or managed hosting from day one?
- How is the underlying software credited without competing with the host's brand?
- How customizable should the chrome be? CSS overrides, theme system, layout templates, or full white-label rebuild?
- What is the upgrade story? Push-button upgrades for managed instances; how is self-hosted upgrade friction kept low?
- How are legal/compliance documents (privacy policy, terms) customized per instance without losing safety defaults?
- What does the contributor experience look like across two instances of the same host (e.g. one host running multiple branded sub-instances)?

## Relationship to existing exploration

The Swish work in [`docks/`](../../docks/Current-Focus.md) is mostly about extension surfaces inside the current monolith. F001 is upstream of that question — once per-host instances exist, host-specific extensions like Swish become natural per-instance concerns rather than platform-wide ones. F001 and [F002](./F002-plugin-architecture.md) together replace the current monolith model.
