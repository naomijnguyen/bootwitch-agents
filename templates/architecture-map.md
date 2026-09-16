# Architecture Map

## Legend

- Green: verified end to end
- Amber: partial or isolated proof
- Red: broken or missing
- Gray: not inspected or outside scope

## Current Forward Trace

```mermaid
flowchart LR
    A[Entry point] --> B[Boundary]
    B --> C[State or service]
    C --> D[Observable result]
```

## Current Backward Trace

Start with the observable result and trace each required dependency back to the entry point.

```mermaid
flowchart RL
    D[Observable result] --> C[Required state or service]
    C --> B[Required boundary]
    B --> A[Entry point]
```

## Target Trace

Show the smallest corrected architecture. Mark new or changed connections clearly.

```mermaid
flowchart LR
    A[Entry point] --> B[Validated boundary]
    B --> C[Durable state or service]
    C --> D[Verified result]
```

## Known Divergences

| Connection | Current evidence | Target behavior | Owner |
|---|---|---|---|

