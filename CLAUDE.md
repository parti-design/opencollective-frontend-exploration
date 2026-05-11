# CLAUDE.md

Instructions for Claude Code working in this repository. Read this file first.

## Context

This is a fork of the Open Collective frontend, used as an exploration repo by a product designer (not a primary OC contributor). The intent is to study the codebase, sketch changes, and build up the thinking that will eventually inform a real fork.

Authoritative behavioral guidance lives in [AGENTS.md](./AGENTS.md) — the `Compass` identity, default exploration mode, collaboration style, and editing guardrails all live there. Follow it.

The notes below add repo-specific operational rules that AGENTS.md does not cover.

## Working wiki

The shared wiki lives under [`docs/wiki/`](./docs/wiki/Home.md). Entry point is `Home.md`. Keep it lightweight and high-signal per AGENTS.md's wiki maintenance rules.

Key sub-sections:

- [`docs/wiki/docks/`](./docs/wiki/Home.md) — current focus, architecture notes, ideas, implementation log. Short-lived working exploration of Open Collective as it exists today.
- [`docs/wiki/transformation/`](./docs/wiki/transformation/README.md) — long-horizon redesign and spec for the new version, in three layers: `pain-points/` (observed) → `patterns/` (structural insight) → `features/` (designed solutions to build).

The two sections cross-reference each other. When `docks/` has prior research relevant to a feature spec, the feature should cite it instead of duplicating it.

### When the user reports a pain point

1. Add it as a new numbered file in `docs/wiki/transformation/pain-points/` (`NNN-short-slug.md`) and update `pain-points/README.md`.
2. Decide whether it fits an existing pattern. If yes, link to it. If it points at a new structural insight, write the pattern under `patterns/` and link both ways. Patterns usually earn a page once two or more pain points point at the same root cause, or when one observation makes the structural picture obvious.
3. If the pattern stabilizes into something the user would actually build, lift the prescriptive shape into a feature spec under `features/` (`FNNN-short-slug.md`) and update `features/README.md`. Features should cite `docks/` research where it exists, not duplicate it.

Keep pain-point entries small: date, role affected, where in the product, what happened, the underlying issue, links. Resist the urge to write a full proposal at the pain-point layer — proposals live in features.

## Git and PR workflow

This repo has two remotes:

- `origin` → `parti-design/opencollective-frontend-exploration` (the user's fork — the working remote)
- `upstream` → `opencollective/opencollective-frontend` (the public OC repo — read-only reference)

Rules:

- **Never push to `upstream`.** It is the public Open Collective repo and is for reference only.
- **Never push directly to `origin/main`.** Always work on a feature branch and open a PR against `parti-design/opencollective-frontend-exploration:main`.
- The `gh` default repo is already set to `parti-design/opencollective-frontend-exploration` so `gh pr create` targets the fork by default. If you ever pass `--repo` or `--base`, double-check it is not `opencollective/...`.
- Branch naming: `claude/<short-topic>` is fine for Claude-driven work. Match the existing style.
- When merging your own PR at the user's explicit request, use `gh pr merge --squash --delete-branch`. Squash keeps `main` history clean.

### A real mistake worth remembering

`gh pr create` from inside a GitHub fork defaults to opening the PR **against the upstream parent**, not the fork itself, even though `origin` points at the fork. This previously caused a PR to be opened in the public Open Collective repo by accident. The `gh repo set-default` fix is in place, but always sanity-check the resulting PR URL before announcing it.

## Collaboration

The user is a product designer with strong product instincts and limited interest in implementation detail for its own sake. Match the tone in AGENTS.md: explain before changing, present tradeoffs, recommend a path, and only implement when explicitly asked.

When the user is in "auto mode" and has told you to act, you can move faster — but the same judgement applies: small, reversible steps; ask before destructive or shared-state actions (push to `main`, force-push, branch deletion the user hasn't asked for, etc.).
