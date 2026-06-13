# Indie Game Dev × C++ — Revenue & Financing Research

Research notes on **how to earn money in game development as a C++ developer
without building a full game end-to-end or working full-time as a game dev**,
plus background on how indie game development gets financed.

Compiled 2026-06-13.

## Contents

| File | What's in it |
|------|--------------|
| [`00-overview-financing-and-revenue.md`](00-overview-financing-and-revenue.md) | How indie dev is financed; the menu of "adjacent" revenue paths (asset packs, freelance, plugins, content, porting). The big-picture orientation. |
| [`01-cpp-gamedev-revenue-deep-research.md`](01-cpp-gamedev-revenue-deep-research.md) | The **deep, cited research**: real best-selling Unreal C++ plugins + prices, unmet-demand forum threads, Godot GDExtension gaps + funding, console-porting reality, optimization/middleware contracting, and a prioritized shortlist of underserved C++-shaped opportunities. Every claim carries a source URL and a confidence rating. |

## How this was produced

The deep-research file is a synthesis of five parallel web-research passes
(one each for: Unreal Fab best-sellers, Unreal unmet-demand threads, Godot
GDExtension demand, console porting, and optimization/middleware contracting).
Claims are tagged **High / Medium / Low** confidence and unverified items are
flagged explicitly.

### Known gaps to re-research later
- **Reddit was inaccessible** to the research tooling (blocked), so r/unrealengine
  / r/godot demand sentiment is *not* verified — re-run with a Reddit-capable fetch.
- **Fab listing pages return 403** to automated fetching and hide prices behind
  login, so several current plugin prices are approximate — confirm logged in.
- **No public sales leaderboard exists for Fab**, so "best-selling" rankings are
  inferred from rating counts + reputation, not hard sales data.
- Several vendor pages (W4 Games, ITJobsWatch, Nintendo/Sony/MS dev portals)
  blocked the fetcher; figures came via search summaries — verify on-page before
  quoting.

## Resuming this work

This folder is self-contained. To continue it in its own private repo:

```bash
mkdir indie-gamedev-cpp-research && cd indie-gamedev-cpp-research
# copy the files from this research/ folder in here
git init && git add . && git commit -m "Initial research bundle"
gh repo create indie-gamedev-cpp-research --private --source=. --push
```

Good next steps are listed at the end of `01-cpp-gamedev-revenue-deep-research.md`.
