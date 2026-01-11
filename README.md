# [Project Name]

> One-line description of what this is.

## Quick Links

- [1-Pager](1-PAGER.md) — Product vision, ICP, growth strategy
- [Backlog](BACKLOG.md) — What's being built
- [System Overview](SYSTEM-OVERVIEW.md) — How agents and skills work

## Getting Started

```bash
# Install dependencies (if any)
npm install

# Run locally
npm run dev

# Deploy
npx wrangler pages deploy ./
```

## Project Structure

```
├── IDEA.md                 # Seed from TinyLabs (deleted after setup)
├── 1-PAGER.md              # Product vision (Planner fills in)
├── BACKLOG.md              # Work queue
├── specs/
│   └── [feature].md        # Feature specs
├── .claude/
│   ├── agents/             # Planner + Builder
│   └── skills/             # Knowledge base (7 skills)
└── src/                    # Application code
```

## Agents

| Agent | What It Does |
|-------|--------------|
| **Planner** | Plans features, maintains backlog, writes specs |
| **Builder** | Builds features, deploys, marks done |

## Working on This Project

1. **To plan:** Ask planner to prioritize or spec a feature
2. **To build:** Ask builder to pick from backlog and build

The backlog is the contract between them.

---

*Built with TinyLabs*
