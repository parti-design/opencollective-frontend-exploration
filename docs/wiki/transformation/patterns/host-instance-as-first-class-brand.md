# Host instance as first-class brand

Back to: [Patterns](./README.md) | [Transformation](../README.md)

## The pattern

Each fiscal host should run their own instance of the platform, branded as their own platform, with the option to extend it for their own context. The platform is software, not a brand. The brand belongs to the host.

This is the WordPress model: WordPress is software that anyone can install; each installation is its own site with its own identity. No one ends up confused about whether they are "on WordPress" — they are on the specific site that runs on WordPress.

Open Collective today is the opposite: one shared installation, one shared brand, with fiscal hosts as tenants inside it. Hosts carry the operational and legal load but get neither the operational control nor the brand benefit.

## Why this matters

The shared-platform model creates three structural costs that show up across many pain points:

- **Brand collapse.** Contributors see three names — collective, fiscal host, Open Collective — for what felt like one gift. Trust takes a hit at every step.
- **No host-level control.** Hosts own the customer relationship but cannot fix platform issues their users complain about. Support load is on the host; the levers are not.
- **Monolithic release cycle.** Host-specific needs (regional payment providers, local compliance, language) require platform-wide changes. The platform's release velocity becomes a ceiling on every host's roadmap.

In return for these costs, the shared-platform model is supposed to deliver cross-host capabilities — but in practice, there are essentially no cross-host features that require everyone to share an installation. The cost is real; the benefit is largely imaginary.

## Proposed shape of the solution

Treat each fiscal host as the operator of their own instance:

- **Own branding.** The host names the platform, sets the look and feel, owns the visible identity. Open Collective (the project) becomes the underlying software, not the public brand.
- **Own deployment.** Each host runs their own installation, like a WordPress site. They control upgrades, configuration, and operational ownership.
- **Own extensions.** Each host can install plugins for the integrations and flows they specifically need, without waiting for the rest of the network.
- **Optional federation.** If real cross-host features ever emerge (cross-host migration, shared identity for repeat contributors), federate them as opt-in protocols between instances. Federation should be a possibility, not a precondition.

The two features that follow directly from this pattern:

- [F001 — Per-host branding and instance](../features/F001-per-host-branding-and-instance.md)
- [F002 — Plugin architecture](../features/F002-plugin-architecture.md)

## What this is not

- Not a rejection of cooperation between hosts. Hosts can still share practices, code, and even data through opt-in mechanisms.
- Not a claim that Open Collective (the project) becomes invisible. It remains visibly the upstream software, the way WordPress is visibly the engine behind millions of sites. But it is the engine, not the brand the contributor interacts with.
- Not free. Per-host instances mean hosts have real operational responsibility for hosting, upgrades, and security. The feature spec for [F001](../features/F001-per-host-branding-and-instance.md) needs to account for managed-hosting options for hosts who do not want to run servers.

## Open questions

- Where does the line fall between "host instance" and "host as a tenant inside a managed deployment"? Some hosts will want full self-hosting, others will want managed hosting with their own brand.
- How is the underlying software credited without competing with the host's brand?
- How is contributor identity handled across instances? Do they re-create accounts per host, or is there a lightweight federation for "I have given before"?
- How are platform-wide standards (data formats, ledger semantics, expense schemas) maintained when each instance is independently deployed and possibly modified?

## Linked pain points

- [002 — Fiscal host owns the relationship but not the platform](../pain-points/002-fiscal-host-brand-confusion.md)
