# 002 — Fiscal host owns the relationship but not the platform

Back to: [Pain Points](./README.md) | [Transformation](../README.md)

- **Date observed:** 2026-05-11
- **Role affected:** Fiscal host (operationally responsible) and contributors (trying to understand who they gave money to)
- **Where in the product:** Across the entire platform — collective pages, transaction emails, bank statements, support touchpoints
- **Related pattern:** [Host instance as first-class brand](../patterns/host-instance-as-first-class-brand.md)
- **Related features:** [F001 — Per-host branding and instance](../features/F001-per-host-branding-and-instance.md), [F002 — Plugin architecture](../features/F002-plugin-architecture.md)

## What happened

As a fiscal host running collectives on Open Collective, we own the customer relationship — contributors, collective admins, and the wider community reach out to us when something is wrong, when they need a receipt, when a payment is stuck. But we cannot actually fix most of the things they ask about because the platform is operated by Open Collective, not by us. We have no backend access, no admin escalation path, no ability to tweak emails or labels for our own users.

At the same time, the customer-facing identity is split three ways:

- The **collective** they thought they were supporting (the visible cause).
- The **fiscal host** that appears on their bank statement (the legal/financial entity).
- **Open Collective** on the web page they donated through (the platform).

Three different names show up across the donation flow and the audit trail. Contributors regularly ask us "who is this?" when they see the host name on their bank statement, and "who is Open Collective?" when we explain how it works. Trust takes a hit at every step.

## Why this is confusing

Open Collective is multi-tenant infrastructure but presents itself as a brand. From the contributor's point of view, three brands are involved in what felt like a single gift. From the host's point of view, the platform's name is more visible to their own community than the host's name — even though the host is the one carrying the legal, financial, and support burden.

The platform is also operationally monolithic: a single shared installation that all hosts share. Hosts cannot customize, extend, or fix anything inside it, even though they are the ones contributors talk to.

## Underlying issue

There is no real reason the platform needs to be operated as a single multi-tenant installation. There are essentially no cross-host features that require everyone to be on the same instance. The shared-platform model imposes costs (brand collapse, no host-level control, monolithic release cycle) without delivering a corresponding cross-host benefit.

This points at two structural changes:

1. Treat each fiscal host as the operator of their own instance, branded as their own platform — see pattern: [Host instance as first-class brand](../patterns/host-instance-as-first-class-brand.md) and feature: [F001](../features/F001-per-host-branding-and-instance.md).
2. Make the platform extensible per-host, so host-specific needs (regional payment providers, local compliance flows, language) can be added without a platform-wide release — see feature: [F002](../features/F002-plugin-architecture.md).

## Notes from the host seat

- Contributors regularly contact the host about platform-level issues we cannot fix.
- Bank-statement descriptors mention the host, which contributors do not recognize because the donation page said "Open Collective."
- The host carries the support load for problems caused by platform decisions outside the host's control.
- Trust friction is biggest with new contributors — the people we most want a smooth first experience for.
