# Agents & Skills System Overview

## Philosophy

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│  THE LLM ERA                                                                    │
│                                                                                 │
│  Building is fast and cheap. Everyone can ship.                                 │
│  The differentiator is DESIGN and DISTRIBUTION.                                 │
│                                                                                 │
│  This system:                                                                   │
│  • Two agents: Planner + Builder                                                │
│  • Skills = detailed knowledge (HOW to do it)                                   │
│  • Growth baked in from day 1                                                   │
│  • Design is the moat                                                           │
│  • Backlog is the contract between agents                                       │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## Project Lifecycle

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│  TINYLABS (before this repo)                                                    │
│                                                                                 │
│  Scouts opportunity → Creates repo from template → Fills in IDEA.md             │
└─────────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  NEW PROJECT (IDEA.md exists)                                                   │
│                                                                                 │
│  Planner reads IDEA.md                                                          │
│      → Researches & fills in 1-PAGER.md                                         │
│      → Defines brand-guidelines                                                 │
│      → Deletes IDEA.md                                                          │
│      → Plans first features                                                     │
└─────────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  ONGOING (1-PAGER.md exists, no IDEA.md)                                        │
│                                                                                 │
│  ┌──────────┐    BACKLOG.md    ┌──────────┐                                     │
│  │ PLANNER  │ ───────────────▶ │ BUILDER  │                                     │
│  └──────────┘                  └──────────┘                                     │
│       │                              │                                          │
│       ▼                              ▼                                          │
│   Plans features              Builds features                                   │
│   Writes specs                Marks done                                        │
│   Prioritizes                 Deploys                                           │
│   Updates 1-pager             Picks next item                                   │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## Key Files

| File | Purpose | Who Owns It |
|------|---------|-------------|
| `IDEA.md` | Seed from TinyLabs. Deleted after setup. | TinyLabs creates, Planner deletes |
| `1-PAGER.md` | Product vision, ICP, growth strategy | Planner creates & maintains |
| `BACKLOG.md` | Work queue | Planner prioritizes, Builder updates status |
| `specs/[feature].md` | Feature specifications | Planner creates |
| `brand-guidelines` | Visual identity | Planner defines |

---

## The Two Agents

### Planner
**Owns WHAT to build and WHEN.**

**New project (IDEA.md exists):**
1. Read IDEA.md seed
2. Research and fill in 1-PAGER.md
3. Define brand-guidelines
4. Delete IDEA.md
5. Plan first features

**Ongoing (no IDEA.md):**
1. Maintain backlog
2. Write specs
3. Prioritize
4. Update 1-pager when product evolves

**Reads:** 1-pager, brand-guidelines, growth-playbook, design-system, product-research

**Triggers:** "plan", "what should we build", "prioritize", "backlog"

### Builder
**Owns HOW to build.**

| Responsibility | Output |
|----------------|--------|
| Pick from backlog | Top priority item |
| Build with quality | Working code |
| Bake in growth | SEO, OG, shareability |
| Deploy | Live site |
| Mark done | Updated backlog |

**Reads:** Specs, brand-guidelines, design-system, ux-patterns, coding-standards, cloudflare-deploy

**Triggers:** "build", "implement", "code this", "ship this"

---

## The Backlog

`BACKLOG.md` is the contract between Planner and Builder.

```markdown
# Backlog

## Up Next
- [ ] **Feature Name** — Description
  - Spec: `specs/feature-name.md`
  - Type: core | growth | monetization | fix

## In Progress
- [ ] **Feature Name** — Description

## Done
- [x] **Feature Name** — Description
```

**Rules:**
- Every item has a spec before building
- Top item = what builder works on next
- Tag items: `core`, `growth`, `monetization`, `fix`
- Planner keeps it current, Builder updates status

---

## All Skills (7)

Skills are the knowledge base. Both agents read them as needed.

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ RESEARCH (1)                                                                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│ product-research        Idea validation, ICP discovery, naming                  │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│ DESIGN (3) — The Moat                                                           │
├─────────────────────────────────────────────────────────────────────────────────┤
│ brand-guidelines        Colors, typography, inspiration (Planner fills)         │
│ design-system           Philosophy + components (Button, Card, Input)           │
│ ux-patterns             Loading, empty, error, success states                   │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│ GROWTH (1)                                                                      │
├─────────────────────────────────────────────────────────────────────────────────┤
│ growth-playbook         Distribution strategies, pSEO, free tools               │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│ DEVELOPMENT (2)                                                                 │
├─────────────────────────────────────────────────────────────────────────────────┤
│ coding-standards        Tech stack, security, code patterns                     │
│ cloudflare-deploy       How to deploy to Cloudflare Pages                       │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## Project Structure

```
project/
├── IDEA.md                     # Seed (deleted after setup)
├── 1-PAGER.md                  # Product vision (filled by Planner)
├── BACKLOG.md                  # Work queue
├── specs/
│   ├── _TEMPLATE.md            # Spec template
│   └── [feature].md            # Feature specs
├── .claude/
│   ├── agents/
│   │   ├── planner.md
│   │   └── builder.md
│   └── skills/
│       └── ... (7 skills)
└── src/                        # Application code
```

---

## Trigger Phrases

| Agent | Triggers |
|-------|----------|
| **planner** | "plan", "what should we build", "prioritize", "backlog", "next feature" |
| **builder** | "build", "implement", "code this", "ship this" |

---

## Quality Bar

**Every build must:**
- ✅ Match brand-guidelines
- ✅ Use design-system components
- ✅ Include loading, empty, error states
- ✅ Be mobile responsive
- ✅ Be accessible
- ✅ Have SEO + growth hooks

**Planner ensures:** Clear specs, prioritized backlog, growth/monetization thinking

**Builder ensures:** Quality execution, no shortcuts, mark done when done
