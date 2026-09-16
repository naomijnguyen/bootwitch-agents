# AGENTS

AGENTS is a reusable coordination system for parallel repository work. It captures the workflow used in the Bootwitch Doctor experiment: map the system, trace it backward from the observable result, assign narrow connections, exchange evidence through shared notes, and reconcile each wave through one integration lead.

## The core idea

Parallel agents are useful when their boundaries are explicit. They become risky when several agents change the same contract while relying on stale assumptions. AGENTS makes those assumptions visible.

Each session has:

- one overview of the goal and acceptance criteria;
- current, backward, and proposed architecture traces;
- bounded assignments for each agent;
- private working notes for each agent;
- an append-only shared ledger for cross-agent messages;
- evidence-backed handoffs;
- one mutable status page maintained by the integration lead.

## Working rhythm

1. **Map before editing.** Record what exists, what the successful result should be, and where the traces diverge.
2. **Fix connections first.** A working component is not enough if the runtime never reaches it.
3. **Assign narrow ownership.** Give each agent a component or connection, owned files, dependencies, and acceptance tests.
4. **Share discoveries without erasing history.** Agents append cross-agent notes and keep detailed work in their own notes.
5. **Verify independently.** A separate reviewer proves the runtime connection and failure behavior.
6. **Reconcile centrally.** The integration lead accepts or rejects claims, redraws the traces, and prepares the next wave.

## Recommended roles

- **Integration architect:** owns the system map, accepted decisions, and final reconciliation.
- **Storage or state agent:** owns persistence contracts, migrations, and durability behavior.
- **Boundary agent:** owns validation, service contracts, and route behavior.
- **Runtime agent:** owns composition, lifecycle, dependency injection, and process boundaries.
- **Verification agent:** owns independent process-level and failure-path tests.

Use fewer roles when the repository is small. Preserve the ownership boundaries even when one person performs more than one role.

## Folder model

```text
AGENTS/
├── SKILL.md
├── OVERVIEW.md
├── ARCHITECTURE.md
├── handoffs/
│   └── shared_notes.md
├── templates/
├── scripts/
└── sessions/
    └── <session-id>/
        ├── OVERVIEW.md
        ├── ARCHITECTURE.md
        ├── STATUS.md
        ├── handoffs/shared_notes.md
        └── agents/<agent-name>/
            ├── ASSIGNMENT.md
            ├── NOTES.md
            └── HANDOFF.md
```

The root shared ledger preserves durable cross-session lessons. A session ledger is scoped to one run. Both are append-only.
