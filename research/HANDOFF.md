# Session Handoff — pick up here in a local Claude Code session

This folder was produced in a **Claude Code on the web** session (2026-06-13).
It's committed to branch `claude/indie-game-financing-spod5u` in
`armahnii2000/libHttpClient` so it can be continued locally. The conversation
history itself does NOT transfer — this doc is the bridge.

## The goal (context)
George (deep C++ background) wants to earn in/around game development **without
building a full game end-to-end or working full-time as a game dev**, and to
understand where he can **contribute** (incl. unpaid) for the biggest impact.
Decided to **start contributing to Godot tomorrow.**

## What's in this folder
- `README.md` — index of the bundle.
- `00-overview-financing-and-revenue.md` — how indie dev is financed + the menu
  of adjacent revenue paths.
- `01-cpp-gamedev-revenue-deep-research.md` — cited deep research (Unreal Fab
  plugins, Godot GDExtension, console porting, optimization/middleware) + a
  prioritized opportunity shortlist. Confidence-tagged.
- `job-search.md` — US C++ games job search: freshest lead, studio portals,
  LinkedIn/board strategy, salary benchmarks.

## Key conclusions reached
1. "Open proposal" ≠ "fillable gap." Three kinds of pending work: (A) engine
   *contribution* (paid via Foundation/W4/bounty, not sold), (B) sellable product
   gaps (rare/crowded in mature engines), (C) contract work (most reliable $).
2. **Godot** is the highest-leverage place to contribute (verified: rendering
   team is understaffed; physics modernization post-Jolt). It converts to paid
   roles later (Foundation/W4/contracts).
3. Mature engines (Unreal) are plugin-saturated — most "gaps" already served;
   real money there is contract/optimization, not empty product niches.
4. Job-site validation limitation: web fetcher is 403-blocked by ATS + LinkedIn;
   validate postings in a logged-in browser (see job-search.md).

## Verified concrete starting points for Godot
- On-ramp reality: Godot barely uses "good first issue" (only ~3 open, one a
  joke). Real path = **Bug Squad** + pick an area you can do, then fix a recent bug.
- Highest-need area = **rendering** (post-processing overhaul, GI/SDFGI) and
  **physics** (node bindings + multithreading).
- Verified-open items to look at:
  - Multithreaded 3D physics — godot-proposals #483 (open, unassigned)
  - Deferred rendering #8295, FSR3 #8768, static/dynamic shadows #4635
  - Real bug w/ good-first-issue label: godot/issues #103676 (gizmo draw calls)
- Also explored O3DE (SIG-organized, under-triaged, AAA-grade C++) and Flax
  (small, fast-merge, 661 open issues) as alternatives.

## Suggested next steps
1. **Godot:** clone godotengine/godot, build it, join the Rendering or Physics
   area (Bug Squad / Discord), pick one recent bug in that area and fix it.
   Trace one render pass end-to-end (RenderingServer → RenderingDevice → shader).
2. **Jobs:** set the LinkedIn alert (job-search.md recipe); apply to the
   thatgamecompany Senior Engine Programmer role if still open.
3. Optional: revisit selling a Godot GDExtension once you know the codebase.

## How to continue this locally
1. Install Claude Code locally (see chat / docs.claude.com).
2. `git clone https://github.com/armahnii2000/libHttpClient.git`
3. `cd libHttpClient && git checkout claude/indie-game-financing-spod5u`
4. Run `claude` in that directory and point it at `research/` — start with this
   HANDOFF.md.
