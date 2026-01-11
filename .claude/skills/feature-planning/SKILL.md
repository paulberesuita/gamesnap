# Feature Planning

Reference for planning features of all types. Add planned features to `BACKLOG.md`.

**Remember:** If a feature changes the product direction, update `1-PAGER.md` too. It's a living document.

---

## Feature Types

| Type | What It Is | Reference Below? |
|------|------------|------------------|
| **Core** | Main product functionality | No — just write a spec |
| **Fix** | Bug fix or improvement | No — just write a spec |
| **Growth** | Drives traffic/users | Yes — see Growth section |
| **Monetization** | Drives revenue | Yes — see Monetization section |

---

## Core Features

No special reference needed. Write a clear spec with:
- Why it matters
- User story
- Requirements
- User flow

---

## Fixes

No special reference needed. Write a clear spec with:
- What's broken or needs improvement
- Expected behavior
- How to verify the fix

---

## Growth Features

Strategies for driving traffic and users.

### Default Growth Playbook

Follow this order:

| Phase | Strategy | Example |
|-------|----------|---------|
| **1** | Programmatic SEO | Pages for "[X] in [city]", "[X] vs [Y]" |
| **2** | Free Tools | Simple calculator, converter, checker |
| **3** | LLM Tools | "Upload your menu, get a grade" |
| **4** | Content | Short-form AI video |

Start with Phase 1. Progress through phases as the product matures.

### Programmatic SEO (pSEO)

Create many pages targeting search patterns:

| Pattern | Example |
|---------|---------|
| `[X] in [city]` | "coffee shops in seattle" |
| `best [X] for [Y]` | "best CRM for startups" |
| `[X] vs [Y]` | "notion vs obsidian" |
| `[X] calculator` | "salary calculator" |

**Find opportunities:** Google autocomplete, People Also Ask, competitor pages.

### Free Tools

One focused tool that solves a specific problem:

| Type | Examples |
|------|----------|
| Converters | File, format, unit |
| Calculators | ROI, salary, cost |
| Generators | Name, text, image |

**Requirements:**
- Works instantly (no signup)
- "Powered by [Product]" badge
- Screenshot-friendly result

### LLM-Powered Tools

| Type | Search Pattern |
|------|----------------|
| Generators | "[X] generator" |
| Analyzers | "analyze my [X]" |
| Recommenders | "what [X] should I use" |

Higher perceived value, natural paywall opportunity.

---

## Monetization Features

| Traffic Level | Strategy |
|---------------|----------|
| 0-10K | Grow, don't monetize |
| 10K-50K | Ads, affiliate links |
| 50K+ | Premium features, paid tiers |

---

## Growth Hooks Checklist

Add to every feature spec (all types):

- [ ] SEO basics — title, meta description, canonical
- [ ] OG tags — image, title, description for sharing
- [ ] Shareability — clean output, share buttons
- [ ] "Powered by" badge (if output is shareable)

---

## Adding to Backlog

After planning a feature, add it to `BACKLOG.md`:

```markdown
## Up Next
- [ ] **Feature Name** — One-line description
  - Type: core | growth | monetization | fix
  - Spec: `specs/feature-name.md`
```

Prioritize ruthlessly — top item is what gets built next.
