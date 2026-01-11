# GameSnap

## Problem
Board game rulebooks are notoriously awful. "Most people can't or won't learn a game by reading the rulebook themselves" — there's an entire side industry (YouTube tutorials, player aids, AI chatbots) just to help people understand how to play. The friction is highest at game night when someone pulls out a game nobody knows, at thrift stores when rules are missing, or when visiting family and finding old games in the closet. People want to play, not study.

## ICP
**Who:** Casual board game players (not hobbyists) hosting game nights, families with kids, people who find games at thrift stores or relatives' houses.

**Problem:** Staring at a game you want to play but nobody knows the rules, and reading the rulebook feels like homework. The "rules explainer" person in every group is burned out.

**Where they hang out:**
- Reddit: r/boardgames, r/boardgamedeals, r/ThriftStoreHauls
- BoardGameGeek forums
- Facebook board game groups
- TikTok/Instagram (casual gaming content)

**Language they use:**
- "The rulebook is god-awful"
- "I have to watch a YouTube video before I can even read the rulebook"
- "We spent 30 minutes trying to figure out the rules"
- "Found this at Goodwill, anyone know how to play?"
- "What game is this?" (photo posts)
- "Rules too complicated"
- "How to play [game name] simple"

**What they've tried:**
- Reading the rulebook (painful, confusing)
- YouTube tutorials (Watch It Played, Gaming Rules!) — 10-20 min videos
- AI chatbots (RulesBot.ai, Boardgamebot.AI, Ludomentor)
- BoardGameGeek forums for clarifications
- Having one person be the "rules master"

**Why those fail:**
- YouTube requires knowing the game name AND 10+ minutes of watching
- AI chatbots require typing the game name (what if you don't know it?)
- AI chatbots give full rules, not "just enough to start playing"
- Rulebooks are reference docs, not learning docs
- None solve the "what IS this game?" problem for thrift finds or old games

## Solution
GameSnap: Snap a photo of any board game box, board, or components — get an instant, simplified "how to play in 2 minutes" guide. The AI identifies the game from the image (even if you don't know the name), then generates a beginner-friendly quick-start guide focused on: goal, setup, turn structure, how to win. Not the full rulebook — just enough to start playing.

**Core flow:**
1. Take photo of game box/board/pieces
2. AI identifies the game (shows confidence + suggests alternatives if unsure)
3. Returns simplified quick-start guide
4. Optional: Ask follow-up questions about specific rules

## Growth Strategy
**Phase 1: Programmatic SEO**
- "How to play [game name] simple" pages for top 1000 board games
- "Quick start guide [game name]" pages
- "[Game name] rules explained simply"
- Target long-tail: people searching for simplified rules, not full rulebooks

**Phase 2: Free Tool**
- Board game identifier from photo (even without rules)
- "What board game is this?" tool
- Missing pieces checker (snap photo, get component list)
- Shareable quick-start guides (host brings up on phone, everyone reads)

**Phase 3: LLM Tool (Core Product)**
- Photo → Instant simplified rules
- Voice mode: "Explain this rule" while playing
- House rules suggestions
- "Teach me like I'm 10" mode for playing with kids

**Phase 4: Content**
- TikTok/Reels: "POV: You found a game at Goodwill" → snap → rules in 30 seconds
- "Board games explained in 60 seconds" series
- "The rules your family always gets wrong" series
- User-generated content from game night moments

## Monetization
**Free tier:**
- 5 scans/month
- Access to all SEO pages (quick-start guides)
- Basic quick-start guide

**Pro tier ($5/month or $30/year):**
- Unlimited scans
- Detailed rules + strategy tips
- Voice mode / follow-up questions
- Save games to personal library
- Offline access to saved games

**Timeline:** Launch free, add paywall after 1000 MAU or clear engagement signal.

## Type
App (PWA) + Website

## Competitive Landscape
| Competitor | What they do | Gap |
|------------|--------------|-----|
| RulesBot.ai | AI chatbot for rule questions | Text-only, need to know game name, gives full rules |
| Boardgamebot.AI | AI rules assistant | Same — no image recognition |
| Ludomentor | AI companion app | Reported as "often wrong," no image scanning |
| Watch It Played (YouTube) | Video tutorials | 10-20 min videos, need to know game name |
| BoardGameGeek | Community + rules PDFs | Not simplified, intimidating for casuals |
| Precision Counter | AI piece identifier | Identifies pieces, not rules |

**Our edge:** Photo-first (don't need to know the game name) + simplified output (quick-start, not full rules).

## Validation Signals
- "Every Board Game Rulebook is Awful" essay went viral on HN and BGG
- YouTube tutorial channels have millions of subscribers (demand for video learning)
- Multiple AI chatbots launched but none do photo recognition
- r/boardgames constantly has "What game is this?" photo posts
- Thrift store gaming is a growing niche (r/ThriftStoreHauls)
- "Quick start guide" is a product category some publishers now include

## Notes
- **Tech stack:** Vision API (Claude/GPT-4V) + RAG on rulebook database
- **MVP scope:** Photo upload → game identification → pre-written quick-start guide (start with top 100 games)
- **Data moat:** Build library of simplified quick-start guides (not just AI-generated each time)
- **Launch angle:** "Shazam for board games" — immediately understandable pitch
- **Risk:** Cold start on game library; mitigate by pre-generating top 100 games before launch
