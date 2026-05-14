# VERTIGO — Platformer Concept

> **Status**: Draft
> **Author**: Game Designer
> **Created**: 2026-05-14
> **Layer**: Foundation · **Priority**: MVP

---

## Overview

VERTIGO is a 2D momentum-driven precision platformer where players ascend a
mysterious, ever-shifting tower. The core verb is **movement**: wall-running,
grappling, dashing, and sliding chain together into a continuous flow. The
tower is not a static level — it rearranges itself in response to the player's
ascent, creating a dynamic obstacle course that no two runs experience the same
way. The game asks one question: *how long can you keep moving?* There is no
combat, no inventory, no dialogue — just the player, the tower, and the
exhilaration of perpetual motion. The player's goal is to reach the summit
before the tower's shifting pathways close off the route, mastering a
momentum-combo system that rewards chaining movement abilities without ever
touching the ground.

**Elevator Pitch**: It's a precision platformer where you chain wall-runs,
grapples, and dashes to ascend a procedurally rearranging tower — stop moving
and the tower closes in around you.

---

## Core Mechanics

### Movement Verbs (The Player's Toolkit)

The player has four movement abilities, each unlocked progressively during the
first run and available from the start of every subsequent run:

| Verb | Description | Input | Cooldown |
| ---- | ----------- | ----- | -------- |
| **Wall-Run** | Run along any vertical surface for up to 2 seconds. Direction depends on the wall's normal — the player sticks to the surface and maintains forward momentum. | Hold toward wall + jump at contact | None (duration-limited) |
| **Grapple** | Fire a grappling hook toward a targeted anchor point. On connect, the player swings in a pendulum arc and can release at any point to launch in the tangent direction. | Aim (right stick / mouse) + trigger | 1.5s |
| **Dash** | Instant burst of speed in any of 8 directions. Provides brief i-frames at the start. Resets on touching the ground. | Direction + dash button | Air: 3s, Ground: none |
| **Slide** | Drop into a slide that preserves downhill momentum and fits through low gaps. Can transition into a dash or jump at any point. | Crouch while moving | None |

### Momentum Combo System

The central system that binds all movement together. The player's current
**Momentum Multiplier** starts at 1.0× and increases by 0.25× each time the
player chains a different movement verb without touching the ground:

- Chaining the **same** verb twice in a row does not increase the multiplier
  (prevents spamming one ability).
- The multiplier applies to **movement speed** and **jump height**.
- Multiplier caps at 4.0× (12 unique verb chains).
- Touching the ground resets the multiplier to 1.0×.
- Visual and audio feedback intensifies with the multiplier — wind lines,
  screen-edge vignette pulse, rising pitch in the movement SFX.

**Design Intent**: The multiplier creates a risk-reward tension. Higher speeds
make navigation easier (bigger gaps become possible) but harder to control
(reaction windows shrink). This pushes the player toward the Flow channel.

### Tower Structure

The tower is divided into **Biomes** — visually and mechanically distinct
vertical zones that the player ascends through in sequence:

| Biome | Height Range | Mechanical Theme | Visual Theme |
| ----- | ------------ | ---------------- | ------------ |
| **Foundry** | 0–300m | Introduces wall-running. Wide corridors, generous anchor points. | Industrial ruins, steam vents, glowing molten metal |
| **Aqueduct** | 300–600m | Introduces grappling. Vertical shafts with water currents that push the player. | Flooded chambers, cascading waterfalls, bioluminescent moss |
| **Spire** | 600–900m | Introduces sliding. Narrow ledges, fragile platforms that crumble on contact. | Crystalline structures, refracting light, high wind |
| **Void** | 900m+ | All abilities tested at maximum intensity. Gravity anomalies, inverted surfaces. | Abstract geometry, starfield backdrop, reality distortion |

### Procedural Rearrangement

The tower is not a fixed level. Each room is a hand-crafted **chunk** (a
pre-built room segment with defined entry/exit points, anchor positions, and
challenge types). Between runs, the tower re-seeds, assembling chunks into a
new vertical sequence. Key properties:

- **Seed-based generation**: The tower layout is deterministic for a given seed,
  enabling speedrun competition and shared seeds.
- **Difficulty ramping**: Early biomes draw from easier chunk pools; later
  biomes introduce tighter timings and more complex verb combinations.
- **Anchor integrity**: Anchor points for grappling are placed manually within
  each chunk, not procedurally — preserving designer intent at the micro level
  while varying the macro sequence.
- **Tower shift events**: At biome transitions, the tower visibly rearranges
  (platforms slide, walls rotate, new paths open/close). This is choreographed
  rather than real-time — the player has a brief window to observe the change
  before proceeding.

### Failure and Recovery

- **Falling**: Falling below the current room's lower boundary returns the
  player to the last **Anchor Platform** (a safe checkpoint at the start of
  each biome). No lives, no game-over — just lost vertical progress.
- **Crush**: If the tower's shifting walls close on the player, they are pushed
  to the nearest safe surface. No damage, no death — just displacement.
- **Time pressure**: A soft timer in the form of the tower's **Encroaching
  Barrier** rises from below. If the player stays still too long, the barrier
  catches up and forces upward movement. The barrier speed scales with the
  current biome (Foundry: slow; Void: aggressive).

### Scoring and Mastery

- **Time to Summit**: Primary score metric. Faster ascents rank higher.
- **Max Combo**: The highest momentum multiplier achieved in a run is tracked
  separately, rewarding technical mastery over raw speed.
- **Style Points**: Optional collectibles (floating motes) placed in
  high-risk, off-route positions reward exploration and mechanical skill.
  Collecting all motes in a biome awards a rank badge for that biome.

---

## Player Fantasy

### Core Emotional Promise

> *You are a traceur ascending a living tower. Every surface is a path. Every
> moment of contact is a choice. When you chain wall-run into grapple into dash
> without touching the ground, you transcend the obstacle course — you become
> the force moving through it. The tower is not your enemy; it is your
> instrument.*

The player should feel: **exhilaration**, **flow**, and **mastery**.

### MDA Analysis

#### Primary Aesthetics (What the Player FEELS)

| Aesthetic | Priority | How We Deliver It |
| --------- | -------- | ----------------- |
| **Challenge** | 1 (Primary) | Precision platforming with escalating difficulty; speedrun leaderboards; mastery is visible through faster, cleaner runs |
| **Sensation** | 2 | Visual feedback of speed (wind lines, screen effects); audio crescendo with momentum multiplier; controller rumble on wall-grabs and dashes |
| **Discovery** | 3 | Procedural tower layouts make every run a new exploration; hidden collectibles reward off-route navigation; each biome reveals new visual themes |
| **Fantasy** | 4 | The player inhabits the role of a traceur — a movement artist in a surreal, vertical world |
| **Submission** | Supporting | The rhythmic flow state of chained movement serves as a meditative, almost trance-like experience at high skill levels |
| **Narrative** | Minimal | Environmental storytelling through biome aesthetics and the implied mystery of the tower; no explicit plot |
| **Expression** | Minimal | Route choice and movement style allow personal expression within the skill ceiling |
| **Fellowship** | N/A | Single-player experience; community exists through leaderboards and seed sharing |

#### Key Dynamics (Emergent Player Behaviors)

- **Route optimization**: Players will discover optimal chunk sequences and
  memorize anchor placements for speedrunning.
- **Risk-reward tradeoffs**: Players will push momentum multipliers into
  increasingly dangerous territory, balancing speed against control.
- **Seed hunting**: The community will share and compete on specific seeds,
  creating a meta-layer of discovery.
- **Style development**: Skilled players will develop signature movement
  patterns — chaining specific verb sequences that look and feel unique.

#### Mechanics-to-Dynamics Mapping

| Mechanic | Intended Dynamic |
| -------- | ---------------- |
| Momentum Multiplier | Encourages verb chaining; creates risk-reward decisions about when to touch ground vs. push higher multiplier |
| Procedural Chunks | Ensures no two runs are identical; drives seed sharing and route discovery |
| Encroaching Barrier | Applies soft time pressure; prevents indefinite stalling; accelerates pacing |
| Anchor Platforms | Lowers frustration from failure; enables quick retry; keeps the player in Flow rather than tilting |
| Hidden Motes | Rewards exploration and mechanical mastery; adds optional depth for completionists |

### Self-Determination Theory Alignment

| Need | How VERTIGO Serves It |
| ---- | --------------------- |
| **Autonomy** | Every surface presents a choice — which verb to use, which route to take, whether to push the multiplier or play safe. The tower offers paths, not prescriptions. |
| **Competence** | The skill ceiling is deliberately high. Players can feel their improvement through faster times, higher combos, and cleaner runs. Feedback is immediate and readable — the multiplier number, the visual speed cues, the time on the clock. |
| **Relatedness** | Single-player focus, but the seed system and leaderboards create a shared language. Players swap seeds, compare routes, and compete on leaderboards. The tower itself serves as an environmental "character" — mysterious, responsive, alive. |

### Flow State Design

- **Onboarding**: The Foundry biome introduces wall-running in isolation (wide
  corridors, generous timing) before combining it with other verbs. The first
  run is a guided ascent — the tower's rearrangement is gentler, and the
  Encroaching Barrier is slow.
- **Sawtooth difficulty**: Each biome escalates challenge through its chunk
  pool, culminating in a biome-finale room that demands the biome's signature
  verb at high intensity. The biome transition provides a brief respite (new
  visuals, Anchor Platform, slower barrier reset) before the next escalation.
- **Feedback clarity**: Every action produces readable consequences within
  0.5 seconds — the multiplier counter ticks up, the screen effects intensify,
  the SFX pitch rises. The player always knows whether they are chaining
  correctly and how close they are to losing the multiplier.
- **Failure recovery**: Falling costs vertical progress but resets the player
  to a known-safe Anchor Platform within seconds. No loading screens, no death
  animations, no punishment beyond lost time. The recovery is fast enough to
  keep the player in Flow.

### Player Type Appeal (Bartle Taxonomy)

- **Achievers**: Time-to-Summit leaderboards, per-biome rank badges from mote
  collection, visible mastery through faster runs.
- **Explorers**: Procedural seed variation, hidden motes in off-route positions,
  biome discovery on first ascent, environmental storytelling.
- **Competitors**: Global and friend leaderboards, seed-based competition,
  speedrun optimization.
- **Socializers**: Seed sharing, route discussion, community leaderboards.
  (The weakest appeal — this is primarily a solo experience.)

---

## Reference Games

| Reference | What We Take From It | What We Do Differently |
| --------- | -------------------- | ---------------------- |
| **Celeste** | Precision platforming feel; tight, responsive controls; failure-as-learning philosophy; screen-by-screen challenge design | Celeste is static levels with narrative; VERTIGO is procedural ascent with no story — pure mechanics focus |
| **Downwell** | Vertical descent as core structure; combo system that rewards chaining actions; minimalist presentation | Downwell is descent; VERTIGO is ascent. Downwell's combo is kill-based; VERTIGO's is movement-based |
| **Neon White** | Speedrunning as core loop; movement verb toolkit; time-based scoring; card/ability metaphor for movement | Neon White is discrete levels with weapon cards; VERTIGO is continuous ascent with innate abilities — no weapons, no cards, no levels, just verbs |
| **Mirror's Edge** | First-person parkour feel translated to 2D sensibility; momentum as the central design principle; clean, readable environments | Mirror's Edge is narrative-driven and hand-crafted; VERTIGO is mechanic-driven and procedural |
| **Tony Hawk's Pro Skater** | Combo system logic — different verbs chain into multipliers; the "one more run" psychology | Transplants combo logic from skateboarding to platforming |

---

## Anti-Pillars (What VERTIGO Is NOT)

- **NOT a combat game**: No enemies, no health bars, no damage. The tower is the
  obstacle, not a combatant.
- **NOT a Metroidvania**: No ability-gating, no backtracking, no item
  collection that unlocks new areas. All movement verbs are available from the
  start of each run after the first.
- **NOT narrative-driven**: There is no dialogue, no cutscenes, no plot. The
  world tells its story through environment and atmosphere alone.
- **NOT a roguelike**: No permanent upgrades between runs, no meta-progression
  systems. The only thing the player carries between runs is their own skill.
