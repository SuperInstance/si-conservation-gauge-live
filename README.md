# si-conservation-gauge-live

> **Live conservation gauge** — real-time fleet budget visualization showing γ/η split across agents.

## What This Is

A single-file HTML+JS dashboard that visualizes the SuperInstance conservation law across the fleet:

```
γ + η = C  (gamma + eta = total_budget)
```

Every agent in the fleet has a cognitive budget. γ (gamma) is the durable, high-value portion. η (eta) is the ephemeral, consumable portion. The total is conserved.

## Features

- **12 fleet agents** with individual γ/η gauges
- **Color-coded status**: green (healthy) → yellow (warning) → red (critical)
- **Fleet-wide summary** bar showing aggregate γ/η split
- **Timeline chart** showing budget history over time
- **Conservation verification** — total line stays flat (the invariant holds)
- **Simulated live updates** — auto-ticks every 2 seconds

## View It

Open `index.html` in any browser. No server needed.

Or visit the GitHub Pages deployment: [SuperInstance Conservation Gauge](https://superinstance.github.io/si-conservation-gauge-live/)

## The Conservation Law

```
γ (gamma) = durable budget — the high-value, long-term information
η (eta)   = ephemeral budget — the consumable, short-term context
C         = total budget — conserved across all operations
```

When an agent spends budget:
1. η is spent first (ephemeral context gets used)
2. When η is exhausted, γ starts declining (the agent is eating into its durable memory)
3. When γ → 0, the agent is exhausted and needs replenishment

The fleet gauge shows this in real-time. When you see yellow/red cards, those agents need attention.

## Connection to Heddle

This is exactly what Heddle's auto-compact does — when the context window fills up:
- η (ephemeral) gets compressed first → auto-compact
- γ (durable) is what survives compaction → the "keep" pile
- C (total) is the token limit → conserved

By visualizing it, we can see which agents are burning through their budget unsustainably.

## Architecture

Pure static HTML + CSS + JavaScript. No build step. No dependencies.

```
index.html  — everything in one file
├── CSS     — dark theme, responsive grid
├── JS      — agent simulation, gauge rendering, timeline
└── Canvas  — budget history chart
```

## Future Enhancements

- [ ] Connect to Supabase fleet registry for real agent data
- [ ] WebSocket for live updates from running agents
- [ ] Hodge decomposition overlay (gradient/curl/harmonic per agent)
- [ ] Conservation law violation alerts
- [ ] Export as PNG/SVG for reports

## License

MIT
