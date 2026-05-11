# Current Focus

Back to: [Wiki Home](../Home.md)

## Active Threads

### Swish and Plugin Architecture

- Goal: understand whether Open Collective could support Swish for incoming payments and reimbursements
- Secondary goal: explore a plugin model that allows regional integrations and platform extensions without breaking the shared data model
- Current status: frontend exploration exists, but true end-to-end support still depends on API and operational changes

### Collaboration Mode

- Default working style should be analysis first, implementation second
- Explanations should connect code decisions back to end user experience and product intent
- The user has strong product opinions and wants help understanding implementation options rather than having code written too quickly

## Likely Next Discussions

- whether Swish is worth pursuing as a real integration or as a structured manual bridge first
- what plugin surfaces Open Collective should expose first
- how to separate core ledger data from extension-specific configuration

## Related Notes

- [Architecture and Constraints](./Architecture-and-Constraints.md)
- [Ideas and Questions](./Ideas-and-Questions.md)
- [Implementation Log](./Implementation-Log.md)
- Forward-looking spec for the plugin direction: [F002 — Plugin architecture](../transformation/features/F002-plugin-architecture.md)
- Forward-looking spec for per-host instances: [F001 — Per-host branding and instance](../transformation/features/F001-per-host-branding-and-instance.md)
