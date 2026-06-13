# C++ Game-Dev Revenue — Deep Research (2025–2026)

**Question:** Where is the *real, current* demand for a C++ developer who wants to
sell plugins/tools or do bounded contract work — **without** building a full game
or going full-time — across (1) Unreal C++ plugins, (2) Godot GDExtension, and
(3) console porting + optimization/middleware contracting?

Every claim below carries a **source** and a **confidence** rating
(High / Medium / Low). Unverified items are flagged. Methodology and gaps are at
the bottom.

---

## 1. Unreal Engine C++ plugins (Fab marketplace)

### 1a. The named "famous" plugins — and a crucial twist
Several of the best-known Unreal C++ plugins are **NOT Fab revenue earners** —
they're free/open-source + Patreon, or sold off-platform:

- **Voxel Plugin** (Phyronnaz / Côme Chilliet) — Voxel Plugin 2 is **$349
  perpetual** (1 yr feature updates, 3 yrs bug fixes/UE upgrades), sold **directly
  on voxelplugin.com, NOT on Fab**, because Fab's licensing couldn't support their
  per-seat scheme. A free legacy version remains on Fab. **[High]**
  - https://docs.voxelplugin.com/resources/licensing · https://voxelplugin.com/
- **RealtimeMeshComponent** (TriAxis Games / "Koderz") — core is **free + open
  source on GitHub** (Patreon/donation funded); a paid **"RMC Pro"** exists on
  Fab. Pro price not verified (login-gated). **[High]**
  - https://github.com/TriAxis-Games/RealtimeMeshComponent
- **VR Expansion Plugin** (Joshua Statzer / "mordentral") — **free + open source**,
  **Patreon-funded**. Runs a large chunk of indie VR games. **[High]**
  - https://github.com/mordentral/VRExpansionPlugin · https://www.patreon.com/mordentral
- **Advanced Sessions Plugin** (mordentral) — **free + open source**; Blueprint
  exposure for online subsystems (Steam, EOS). **[High]**
  - https://github.com/mordentral/AdvancedSessionsPlugin
- **Dungeon Architect** (Code Respawn / Ali Akbar) — active **paid** on Fab,
  ~4.4/5 over ~263 ratings, at v3.4 (Jan 2026). Price login-gated. **[Med-High]**
  - https://www.fab.com/listings/0ad73dc2-3daa-4c29-a70a-61fb9cea0c7c
- **Electronic Nodes** (Hugo Attal) — editor wiring tool, **$14.99** (seen ~$10.49
  on sale), ~4.9/5 over ~454 ratings. **[High on rating; price sale-dependent]**
  - https://www.fab.com/listings/d6148766-27b1-47db-a730-832c53b7a895

> **Lesson:** the most celebrated C++ plugins monetize via **Patreon + off-platform
> sales**, not Fab unit sales. Don't assume "list on Fab" is the model.

### 1b. Categories that actually sell (paid)
- **Platform SDK integrations are the dominant paid category:**
  - **SteamCore / SteamCore PRO** (eeldev) — full Blueprint Steamworks access. **[High]**
    https://www.fab.com/listings/d101542d-2534-4b2c-be16-e9b3e5cd4d04
  - **EOS Integration Kit / EIK** (Betide Studio) — **$54.99 individual / $129.99
    pro** (price from a secondary blog — verify). **[Med-High]**
  - **EOS Online Subsystem** (Redpoint Games) — free + paid console/crossplay tiers.
- **Multiplayer/networking** (e.g. "Ultimate Multiplayer Lobby") — strong paid category.
- **Editor/workflow tools** and **procedural generation** — perennial sellers.
- ⚠️ **No public Fab sales leaderboard exists**, so "best-selling" is inferred from
  rating counts + reputation, not sales data. **[Flagged — not directly falsifiable]**

### 1c. Fab revenue split & the migration
- **88/12 split** (sellers keep 88%), carried over from Epic Games Store terms. **[High]**
  - https://www.gamedeveloper.com/marketing/epic-to-unify-content-marketplaces-and-offer-creators-88-percent-revenue-cut
- **Migration to Fab launched ~Oct 2024**, unifying UE Marketplace, Quixel,
  Sketchfab, ArtStation Marketplace. Launch incentive: 100% rev share through end
  of 2024. **[High]**
- **Seller complaints are well-documented** (primary forum/seller sources):
  removal of Q&A/review sections eroded buyer trust; **degraded discoverability**
  (no "new releases"); sales drops (one seller: 1–3 sales/week for 2 years → **zero
  in Jan 2025**); a flood of low-quality/AI/copyright content from merged stores.
  Individual figures are anecdotes, not platform-wide stats. **[High that complaints
  are widespread; specific drops are illustrative]**
  - https://techarthub.com/my-unreal-marketplace-journey/
  - https://forums.unrealengine.com/t/no-fab-sales-in-january-2025-any-one-else-experiencing-this/2279155

### 1d. What Unreal devs are actively asking for that doesn't exist (Epic forums)
> ⚠️ Reddit was blocked to the tooling, so these are anchored to **Epic Developer
> Community forum** threads, not Reddit.

- **Drop-in persistence / accounts / leaderboard backend.** Recurring "what are my
  options" threads; answer is always "roll your own SQL + API." **[High pain;
  Med that a plugin vs. hosted service is the wanted form]**
  - https://forums.unrealengine.com/t/best-place-to-store-player-data-for-mmo-dedicated-server/678709
  - https://forums.unrealengine.com/t/data-persistence-and-leaderboards/1332734
- **OSS-agnostic dedicated-server ↔ master-server ↔ DB orchestration** — people
  want a session/server-management layer *without* EOS/Steam. **[High]**
  - https://forums.unrealengine.com/t/dedicated-servers-master-server-and-databases-interactions/1685255
  - https://forums.unrealengine.com/t/multiplayer-mmo-using-dedicated-servers-without-online-subsystems-eos-or-steam/773198
- **Reference-stable, versioned save system for whole actors.** Built-in SaveGame
  doesn't handle actor instances/BP structs/data-asset refs; renamed data assets
  invalidate old saves. Existing paid solutions (SaveExtension/Savior) don't fully
  cover the **versioned, reference-stable, networked** edge. **[High — strongest
  "a plugin could solve this cleanly" candidate]**
  - https://forums.unrealengine.com/t/can-i-save-actors-whole-data/359515
  - https://forums.unrealengine.com/t/serialization-deserialization-of-reference-to-data-asset-for-save-file/2268065
- **Higher-level replication helpers** — per-client/per-property relevancy and
  animation replication are the most-complained-about C++ subsystem. **[High
  complaint volume; Med that a generic plugin beats Epic's own Iris/ReplicationGraph]**
  - https://forums.unrealengine.com/t/why-is-animation-replication-so-hard/155780
  - https://forums.unrealengine.com/t/networking-is-per-client-custom-replication-possible-per-actor-or-per-property/124554
- **World Partition + multiplayer streaming is fragile (2024–2026).** Race
  conditions between WP streaming and net relevancy ("actors fall through the
  world"), Iris failures on cell unload. Newer pain, no clean fix. **[High it's an
  active pain; Low/Med that a 3rd-party plugin vs. engine fix is realistic — but
  signals where large-world teams bleed]**
  - https://forums.unrealengine.com/t/race-condition-between-world-partition-streaming-and-actor-net-relevancy-cause-actors-to-fall-through-the-world/2599296
- **Robust async-loading / hitch-free streaming helper.** "Async Load Asset is
  really unstable"; hitches even when done "correctly." **[Med-High]**
  - https://forums.unrealengine.com/t/async-load-asset-is-really-unstable/1944700
- **EOS/Online Subsystem is considered too complex out-of-box** — a whole cottage
  industry of wrapper plugins (EIK, EOSCore, Redpoint) is itself the demand signal;
  crossplay (Steam↔Epic) fails repeatedly. **Already partially served** — the
  opening is console/crossplay-certified, well-documented wrappers. **[High demand;
  partially served]**

---

## 2. Godot GDExtension / C++ for Godot

### 2a. godot-jolt — the proof point
- **godot-jolt is a C++ GDExtension wrapping Jolt physics** (~93% C++), maintained
  by **Mikael Hermansson ("mihe")**, a **W4 Games** employee, with help from Jolt
  author Jorrit Rouwe. **[High]**
  - https://github.com/godot-jolt/godot-jolt · https://github.com/godotengine/godot-proposals/issues/7308
- **Built as a ~2-year personal project; the final year (the engine-port work) was
  sponsored by W4 Games.** **[Med-High — confirm exact wording on Hermansson's own
  post before quoting verbatim]**
- **Godot 4.4 (March 2025) absorbed Jolt as a built-in engine module** (experimental,
  doesn't yet replace default Godot Physics); the GDExtension is now maintenance-only.
  The "officially endorse godot-jolt" proposal #7308 was effectively fulfilled by
  core integration. **[High]**
  - https://godotengine.org/releases/4.4/ · https://github.com/godot-jolt/godot-jolt

> **The model:** a single C++ GDExtension became the de-facto 3D physics solution,
> got a paid sponsor (W4) for the final push, then was absorbed into the engine.

### 2b. Native capabilities Godot still lacks (real open proposals)
- **Video playback/decoding is the clearest gap.** Native `VideoStreamPlayer`
  supports only deprecated Ogg Theora — no good compression, seeking, or hardware
  decode. Active proposals to move video to an official FFmpeg-based GDExtension.
  **[High]**
  - https://github.com/godotengine/godot-proposals/issues/3286 (FFmpeg GDExtension)
  - https://github.com/godotengine/godot-proposals/issues/12864 · .../7062
  - **Two C++ FFmpeg GDExtensions already monetize this gap:** **EIRTeam.FFmpeg**
    (Álex Román Núñez / EIRTeam, funded via Patreon + sales of *Project Heartbeat*)
    and **GDE GoZen** (sold on itch.io). **[High]**
    - https://github.com/EIRTeam/EIRTeam.FFmpeg · https://voylin.itch.io/gde-gozen-video-playback-addon-for-godot
  - ⚠️ Could **not** confirm any "Foundation-funded official video addon" — evidence
    points to self-funded. **[Unverified — flagged]**
- **High-level multiplayer/networking is single-threaded** (polling on the main
  thread = a real perf ceiling). A C++/threading task. **[High]**
  - https://github.com/godotengine/godot-proposals/issues/1675
- **Threading/perf for scene nodes** — multithreaded AnimationPlayer (100+ animated
  enemies), lock-free MPMC thread pools, async framework. **[Med-High]**
  - https://github.com/godotengine/godot-proposals/issues/12759 · .../discussions/9363
- **First-class C++/GDExtension tooling is itself demanded** (GDScript bottlenecks
  on voxels / large NPC counts). **[Med-High]**
  - https://github.com/godotengine/godot-proposals/issues/13796 · .../13972
- Rank proposals by votes via https://godot-proposals-viewer.github.io/ (tooling pointer).

### 2c. Console export — a real paid third-party market
- **Godot has no first-party console export; the official path is third-party
  middleware.** **[High]** — https://godotengine.org/consoles/
- **W4 Games sells "W4 Consoles"** — middleware-approved Switch / Xbox Series X|S /
  PS5 ports optimized for Godot 4.3+. Pricing not public (contact sales). **[High on
  existence/platforms; Unverified on price]**
  - https://www.w4games.com/w4consoles
- **Lone Wolf Technology** offers Switch / PS4 / Xbox One porting + publishing
  services for Godot games. **[Med-High]**
- (Note: "Pirate Software" is *not* a Godot porting vendor — exclude.)

### 2d. Funding scale (it's real money, not theory)
- **Godot Development Fund: ~€35,992/month** from 1,521 members + 18 sponsors
  (Aug 2025); one-time 2024 donations > €100k. Foundation explicitly **hires
  developers** for engine work *including the C++ GDExtension/godot-cpp bindings*.
  **[High — figure will drift; verify live]**
  - https://fund.godotengine.org/ · https://godot.foundation/2025/01/07/how-we-calculate-donations/
- **JetBrains became a Platinum sponsor** (Aug 2025). **[Med]**
- **W4 Games raised $15M (Dec 2023)** — founded by Godot co-founders Linietsky,
  Verschelde, Alessandrelli — commercializing Godot (console ports, multiplayer/cloud
  middleware). Later reporting also cites an $8.5M round. **[Med-High]**
- **Solo GDExtension devs monetize via Patreon + paid products** (EIRTeam's Heartbeat
  funds the FFmpeg work; GoZen on itch). Amounts not public. **[High on model]**

---

## 3. Console porting + optimization/middleware contracting

### 3a. Switch 2 created a real porting demand spike
- **Switch 2 launched June 5, 2025**; 3.5M+ units in 4 days (fastest-selling
  Nintendo console in US history), 6M+ by Aug 2025. **[High]**
- **~10 of ~25 day-one titles were ports** of games that never hit Switch 1
  (Cyberpunk 2077, Split Fiction, Hitman WoA, Street Fighter 6); described as a
  "port machine." **[High]**
  - https://www.gamespot.com/articles/in-the-switch-2s-first-year-every-third-party-port-tells-a-story-about-the-system/1100-6536987/
- **Caveat that sharpens it:** a **devkit shortage** throttled smaller studios
  through 2025; Nintendo steered small devs to Switch 1 and rationed Switch 2 kits.
  Reportedly easing by Dec 2025 (insider), disputed Feb 2026. So the bottleneck has
  been **access/approval more than a shortage of work.** **[Med — insider/leak sourced]**
  - https://gamerant.com/nintendo-switch-2-third-party-games-lack-of-dev-kits/

### 3b. Porting houses that take contract work (the realistic route in)
- **Sickhead Games** (Dallas) — porting-for-hire; Stardew Valley, Slay the Spire,
  Darkest Dungeon, TowerFall; serves "solo indies to major publishers," ~4–6 mo
  projects. **[High]** — https://www.sickheadgames.com/
- **Tantalus Media** (now Keywords), **Iron Galaxy**, **QLOC** (2,500+ projects),
  **Virtuos** (3,700+ devs), **Saber Interactive**, **Panic Button** (known for hard
  Switch ports). **[High these exist; contract work often flows through large orgs]**
  - https://q-loc.com/ · https://www.virtuosgames.com/our-services/game-development/

### 3c. Devkit / NDA access — the actual barrier (the crux)
- **Nintendo:** registration is **free** and open to "Individual," but a Switch /
  Switch 2 devkit requires an **approved Access Request** (dev history + a *planned
  project*); approval is selective and criteria are opaque. "Register free" ≠ "get a
  Switch 2 kit." **[High that approval is gated]**
  - https://developer.nintendo.com/register
- **Sony (PS5):** must be a **legal entity** (in Europe, sole traders can qualify
  with passport age proof); PlayStation Partners registration, signed NDA,
  corporate-domain email, static/VPN IP, project pitch; devkits loaned free to
  approved partners. **[Med — secondary sources; Sony's portal is gated]**
- **Xbox (ID@Xbox):** must sign in with an **organization** account (not personal);
  concept approval (~10–15 business days), NDA, then 2 free devkits; no fee.
  **[Med-High — Microsoft docs via search summary]**
- **Bottom line:** you generally **cannot get console devkits as a freelancer on
  spec**. The practical path is being **employed/contracted by an already-licensed
  studio** (porting house / publisher) that holds the NDA + devkits. **[High
  directional]**

### 3d. Optimization & middleware contracting (no devkit gate)
- **Paid optimization market is vendor-validated:** **Unity sells "Games
  Consulting"** explicitly covering frame rate, memory, binary size, load time.
  Independent optimization consultancies (e.g. Amunis) sell CPU/GPU/RAM audits.
  Staffing firms (WorkGenius) place C++/Unity/Unreal contractors. **[High]**
  - https://unity.com/products/games-consulting
- **C++ middleware demand is real across four sub-areas:**
  - **Physics** — **Jolt Physics** (Jorrit Rouwe, Guerrilla) ships in *Horizon
    Forbidden West* & *Death Stranding 2*, now Godot 4.4's physics. Top-tier demand
    for the *skill*; a formal paid Jolt **support contract** was **not found**.
    **[High skill demand; support offering unverified]**
    - https://github.com/jrouwe/JoltPhysics
  - **Audio** — Wwise/FMOD integration is a live contract category (ZipRecruiter
    Wwise listings; Upwork FMOD marketplace). **[Med-High existence; rate band broad]**
  - **Networking** — rollback netcode niche, but **GGPO is now free/MIT**; money is
    in implementation/products (Rollback Core Pro, SnapNet). **[Med]**
  - **Nav-mesh/pathfinding** — Recast/Detour is the zlib standard; **Kythera AI** is
    a paid commercial nav/AI vendor with named AAA/indie clients. **[High]**
    - https://github.com/recastnavigation/recastnavigation · https://www.kythera.ai/
- **Funded OSS engine work is real:** Godot Fund (~€36k/mo) hires for godot-cpp;
  **O3DE** is Linux-Foundation funded (Microsoft, Adobe, AWS, Intel, Niantic). **[High
  for Godot; Med for O3DE budget]**
- ⚠️ **Bounty-funded C++ game-engine work:** infrastructure exists (IssueHunt,
  Polar.sh, GitHub Sponsors) but **no concrete currently-funded engine bounty
  examples found** — only proposals. **[Low / largely unverified]**
- **Native C++ plugins inside Unity** are a documented first-class mechanism (cut GC
  / IL2CPP overhead, access intrinsics) — a legitimate reason studios pay for C++
  inside C# projects. **[High mechanism; Med paid-demand volume]**

### 3e. Rates (treat as proxies — weakest-sourced section)
- **UK contract senior C++ ≈ £800/day** median (ITJobsWatch, 6 mo to ~May 2025);
  London senior ≈ £725/day; remote/hybrid ≈ £450/day. **General C++, not
  game-specific.** **[Med — reputable aggregator, not directly fetched]**
  - https://www.itjobswatch.co.uk/contracts/uk/senior%20c++%20developer.do
- **US freelance C++** ~$75–$160/hr generally; game-dev-specific NA cited ~$50–$100/hr.
  **[Low — recruiting/marketing blogs]**
- **No reliable porting-specific contract day rate found.** Do **not** quote one as fact.

### 3f. Real contract/freelance postings (such roles exist)
- **Alderon Games** (remote) — "contracting experienced porting programmers" for all
  5 current consoles, UE4. **[High for existence]**
- **AREA 35** — Platform Programmer (Switch), C++ + UE5, profiling/frame-time/memory
  budgeting, platform compliance. **Panic Button** — Senior/Lead porting engineer.
- Boards: Hitmarker, gamejobs.co, remotegamejobs.com, workwithindies.com.
- ⚠️ Most are **full-time or long-term contract at licensed studios**, not spec
  freelance — consistent with the devkit-access reality (3c).

---

## Prioritized shortlist — most underserved, C++-shaped, demand-backed

Ranked by signal strength × how poorly currently served × fit for "not a full game,
not full-time":

1. **Unreal: reference-stable, versioned save/load for whole actor graphs.**
   Strongest "a plugin could solve this cleanly" signal; existing paid solutions miss
   the versioned/reference-stable/networked edge. Plugin-shaped, off-platform-sellable.
   *(§1d)*
2. **Unreal: OSS-agnostic dedicated-server + persistence + accounts/leaderboard
   backend.** Recurring "just let me wire servers to a DB" gap; only heavy hosted
   services exist today. Could be plugin + optional hosted tier. *(§1d)*
3. **Godot GDExtension filling a critical native gap (video/FFmpeg, threaded
   networking, perf nodes).** Proven model (godot-jolt → W4 → core; EIRTeam/GoZen
   monetizing video). Fundable via Foundation hire, Patreon, or paid addon. Least
   competition of the three engines. *(§2)*
4. **C++ optimization / middleware contracting (physics, nav, audio integration).**
   No devkit gate, vendor-validated paid market (Unity Consulting, Kythera), best
   $/hour, bounded engagements. The "cash-bump" lane between plugin work. *(§3d)*
5. **Unreal: console/crossplay-certified, well-documented EOS/online wrapper.**
   Demand proven by the wrapper cottage industry; partially served, so differentiate
   on console-certification + docs. *(§1d)*
6. **Console porting — via a licensed porting house, not solo-on-spec.** Real,
   Switch-2-boosted demand, but devkit/NDA access gates individuals; realistic entry
   is contracting *through* Sickhead/Panic Button/Alderon-type studios. *(§3a–3c)*

### The pattern that fits a deep-C++ dev
Ship **one focused, genuinely-hard-to-build C++ plugin or GDExtension** (an Unreal
save/backend tool, or a Godot native gap), make it load-bearing, attach
**Patreon/sponsors + off-platform sales** (the Voxel/VR-Expansion/godot-jolt model —
*not* relying on Fab unit sales), and let it double as the portfolio piece that pulls
in **optimization/middleware contracts** (and eventually porting work via a studio)
when you want a cash spike. Plugin = trickle + storefront; contracts = spikes.

### Single highest-signal validation move
Browse Fab's top **Code Plugins** by rating count, and scan the Epic forum +
Godot proposals threads linked above for unanswered "is there a plugin/native
feature that does X." Those unanswered asks *are* the demand list.

---

## Methodology & limitations
- Synthesis of **five parallel web-research passes** (Unreal best-sellers; Unreal
  unmet demand; Godot GDExtension; console porting; optimization/middleware).
- **Reddit was blocked** to the tooling — r/unrealengine / r/godot sentiment is
  **unverified**; re-run with a Reddit-capable fetch.
- **Fab listing pages 403 the fetcher and hide prices behind login** — several plugin
  prices are approximate.
- **No public Fab sales leaderboard** — "best-selling" is inferred from ratings +
  reputation, not sales volume.
- Vendor/portal pages (W4 Games, ITJobsWatch, Nintendo/Sony/MS dev portals, live
  Godot Fund counter) **blocked the fetcher**; figures came via search summaries —
  verify on-page before quoting.
- **Rates are the weakest-sourced data** here; treat all as proxies.

### To independently confirm before relying on
1. Exact wording of Hermansson's statement that W4 sponsored the godot-jolt engine port.
2. Whether any FFmpeg Godot addon is Foundation-funded/official (evidence: self-funded).
3. W4 Consoles pricing; Lone Wolf's current platform list.
4. Current live Godot Fund total; W4's $8.5M vs $15M round details.
5. Current Fab prices for Dungeon Architect, RMC Pro, EIK (login-gated).
6. Reddit demand sentiment (blocked here).
