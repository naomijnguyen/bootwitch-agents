---
name: agents
description: Coordinate multiple coding agents working on one repository through bounded assignments, architecture traces, append-only cross-agent notes, evidence-backed handoffs, and a single integration lead. Use when starting or continuing a parallel repair, migration, audit, or implementation session where agents share dependencies or a working tree.
---

# AGENTS

Use this skill to run multi-agent work as an evidence-producing system. Keep each agent's ownership narrow, make dependencies visible, and let one integration lead reconcile the whole repository.

## Start a session

1. Read `OVERVIEW.md` and `ARCHITECTURE.md`.
2. Create a session under `sessions/` with `scripts/start_session.sh` or copy the templates manually.
3. Record the current architecture, backward trace, target architecture, and acceptance gates before assigning implementation.
4. Give each agent one bounded component or connection and its own `ASSIGNMENT.md`, `NOTES.md`, and `HANDOFF.md`.
5. Name one integration lead. Only that lead updates the session's mutable `STATUS.md` and canonical architecture after reviewing evidence.

## Coordinate agents

- Agents edit only their owned files unless the integration lead expands scope.
- Each agent records detailed discoveries in its own `NOTES.md`.
- Cross-agent dependencies, contract changes, conflicts, and urgent findings go into the session's `handoffs/shared_notes.md`.
- Shared notes are append-only. Never edit, reorder, or delete an earlier entry. Correct an error by appending a new entry that names the superseded entry.
- Use `scripts/append_shared_note.sh` when possible so concurrent writers do not overwrite one another.
- A shared note is a report, not an accepted contract. The integration lead records accepted decisions in `STATUS.md`.
- Keep Git staging, commits, merges, rebases, and pushes serial when agents share a checkout.

## Require evidence

For each handoff, require:

- the observed entry point and call path;
- the state owner and lifetime;
- the connection added, removed, or redirected;
- success and failure-path tests;
- full-suite results when available;
- remaining unknowns and the recommended trace update.

Do not mark a connection green because its two endpoints work independently. Mark it green only after an end-to-end test proves the connection.

## Reconcile a wave

1. Read every agent handoff and all shared-note entries since the previous checkpoint.
2. Review claims against diffs, tests, and runtime evidence.
3. Update `STATUS.md` with accepted decisions, verified connections, and unresolved risks.
4. Redraw both the forward and backward traces.
5. Assign the next smallest set of broken connections.

Use `templates/` for the canonical note formats. Use `handoffs/shared_notes.md` as the cross-session append-only ledger for durable lessons that should survive individual runs.

## Guardrails

- Do not publish, deploy, merge, or push unless the user explicitly asks.
- Do not silently rewrite another agent's notes.
- Do not confuse unit coverage with runtime integration.
- Preserve unknowns as unknowns; never convert an assumption into a verified fact.
- Keep private interview or study material outside public project documentation.

