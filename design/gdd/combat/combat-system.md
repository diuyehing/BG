# VERTIGO — Combat System GDD

> **Status**: Draft
> **Author**: Game Designer
> **Created**: 2026-05-14
> **Layer**: Foundation · **Priority**: TBD (see Design Tension note below)

---

## Design Tension Note

The existing [Platformer Concept GDD](../platformer/platformer-concept.md) declares:
> "NOT a combat game: No enemies, no health bars, no damage."

This combat GDD is written as a **directional exploration**. If combat is added to
VERTIGO, it must not compromise the movement-first identity. This document
proposes a combat model that **extends movement rather than interrupts it** —
combat as parkour, not combat as a separate mode. The Creative Director and team
should decide whether to integrate this system, keep the game combat-free, or
evolve the platformer concept to accommodate both.

---

## Overview

The VERTIGO combat system treats combat as an **extension of movement, not a
separate activity**. Enemies are not health-sponge obstacles that stop the player
in place — they are **moving environmental hazards** that the player neutralizes
by applying their momentum toolkit. There is no "attack button." Damage is
delivered through the same verbs the player already uses: a dash becomes a
tackle, a wall-run becomes a flank, a grapple becomes a pull, a slide becomes a
sweep. Combat rewards **speed, creativity, and chain variety** — the same skills
the core game already teaches.

The design principle is: **if combat requires the player to stop moving, it
fails.** Every combat action must preserve or generate momentum. Enemies exist
to complicate navigation, not to gate progress behind mandatory kills. The
player can bypass, outrun, or neutralize enemies — all three are valid routes,
and the choice depends on the player's current momentum state, route preference,
and skill.

Key numeric targets (preliminary):
- **Time-to-neutralize (TTN)**: 0.8–2.0 seconds per enemy — fast enough to
  maintain flow, long enough to register as a meaningful action.
- **Momentum cost of engagement**: near-zero. The player should exit a combat
  interaction with the same or greater speed than they entered it.
- **Enemy density**: 1–3 enemies per chunk maximum, placed at natural route
  junctions, never in corridors where bypass is impossible.

---

## Player Fantasy

### Core Emotional Promise

> *You don't stop to fight. You flow through threats the same way you flow
> through the tower — turning enemies into stepping stones, obstacles into
> opportunities. When you wall-run past a sentry, grapple it off its perch, and
> dash through two more without touching the ground, you're not fighting. You're
> expressing mastery through motion. The tower tried to put something in your
> way. You turned it into speed.*

The player should feel: **unstoppable**, **fluid**, and **clever**.

### MDA Analysis

#### Primary Aesthetics (What the Player FEELS)

| Aesthetic | Priority | How Combat Delivers It |
| --------- | -------- | ---------------------- |
| **Sensation** | 1 (Primary) | The audiovisual payoff of neutralizing an enemy at speed — screen shake, particle burst, momentum surge — delivers kinesthetic satisfaction. Combat is another texture of movement, not a break from it. |
| **Challenge** | 2 | Enemy placement adds spatial puzzles to navigation. A sentry on a wall isn't a "fight" — it's a routing constraint: do you dash through, grapple past, or slide under? Each option has different momentum outcomes. |
| **Expression** | 3 | No single "correct" way to handle an enemy. The player's choice of verb, approach angle, and chain sequence is personal style. Two players at the same skill level should solve the same enemy placement differently. |
| **Fantasy** | 4 | The player as an untouchable traceur — so fast, so fluid that the tower's defenses can't even register. Enemies are slow relative to a skilled player; the fantasy is being a ghost they can't catch. |
| **Discovery** | Supporting | Enemy types with different behaviors create discovery moments — learning that a Charger can be baited into breaking a wall, or that a Drone's scan beam reveals hidden platforms. |
| **Submission** | Minimal | The rhythmic quality of chaining enemy neutralizations into movement combos can contribute to the meditative flow state at high skill. |
| **Narrative** | Minimal | Enemy presence is environmental storytelling — *what are these things? Why does the tower have defenses?* — answered through design, not exposition. |
| **Fellowship** | N/A | Single-player experience. |

#### Key Dynamics (Emergent Player Behaviors)

- **Route optimization with threats**: Players will discover that neutralizing
  specific enemies at specific angles launches them into optimal approach
  vectors for the next chunk. Enemies become part of the speedrun route, not
  obstacles to it.
- **Enemy juggling at high skill**: Elite players will chain enemy
  neutralizations into their momentum combos, using enemies as additional
  "verbs" — a grapple-kill that preserves the multiplier, a dash-through that
  adds to the chain.
- **Bypass vs. neutralize decision**: Players will constantly evaluate whether
  engaging an enemy gains them enough momentum to justify the path deviation.
  Sometimes the fastest route is to ignore everything. Sometimes the fastest
  route is through them.
- **Threat-as-tool discovery**: Explorers will discover that certain enemy
  behaviors can be exploited to reach hidden areas (a Charger's charge breaks a
  cracked wall; a Drone's patrol path reveals an invisible platform).

#### Mechanics-to-Dynamics Mapping

| Mechanic | Intended Dynamic |
| -------- | ---------------- |
| Verb-as-attack (no dedicated attack button) | Keeps the player in the movement mindset; eliminates the cognitive mode-switch between "moving" and "fighting" |
| Momentum gain on neutralize | Makes combat net-positive for speed; removes the incentive to always bypass |
| Enemy placement at route junctions | Creates spatial decisions, not combat encounters; the enemy is a navigation puzzle |
| Multiple valid approaches per enemy type | Enables personal expression and style development |
| Enemy behaviors that interact with the environment | Creates discovery moments and deepens the systemic layer |

### Self-Determination Theory Alignment

| Need | How Combat Serves It |
| ---- | -------------------- |
| **Autonomy** | Three valid approaches to every enemy placement: bypass (preserve route), neutralize (gain momentum), exploit (use enemy as tool). No "correct" answer. The player chooses their relationship to threats. |
| **Competence** | Mastery is visible and granular. A beginner dashes through enemies. An expert grapples one enemy into another, wall-runs off the explosion, and lands at 3.5× multiplier. The skill expression ceiling is deliberately high. |
| **Relatedness** | The enemies give the tower a sense of being *alive* and *hostile* — not just a static obstacle course, but a place that reacts to the player's presence. This deepens the player's relationship with the tower as an environmental character. |

### Flow State Design

- **No combat mode-switch**: The player never enters a "combat state." There is
  no arena lock, no battle music, no UI change. Combat is continuous with
  movement — the flow never breaks.
- **Feedback within 0.5 seconds**: Neutralization feedback (particle burst, SFX,
  momentum surge) is immediate and visceral. The player knows they succeeded
  before they've finished the motion.
- **Failure recovery is proportional**: Misjudging an enemy approach might cost
  the player their momentum multiplier (touching ground) or knock them off
  course (losing vertical progress). It does not kill them, stop them, or
  trigger a retry. The cost is speed, not progress.
- **Sawtooth via enemy pacing**: Enemy density and complexity follow the same
  sawtooth as the tower biomes — introduced in isolation, combined with other
  challenge types, then tested at maximum intensity before a biome-transition
  respite.

### Player Type Appeal (Bartle Taxonomy)

- **Achievers**: Faster neutralizations = faster times. Mastery of enemy
  interactions is directly measurable on the leaderboard.
- **Explorers**: Enemy behaviors that interact with the environment create
  discovery depth. Can a Charger break *that* wall? Does a Drone reveal
  *this* secret?
- **Competitors**: Enemy routing becomes part of speedrun optimization. The
  fastest route through a chunk may require neutralizing specific enemies at
  specific angles — a new layer of competition.
- **Socializers**: Shared discoveries about enemy interactions; "did you know
  you can grapple a Drone into a Charger?" moments that spread through the
  community.

### Quantic Foundry Motivation Alignment

| Motivation | Combat Contribution |
| ---------- | ------------------- |
| **Action (Excitement)** | High-speed neutralizations deliver visceral, moment-to-moment excitement |
| **Mastery (Strategy)** | Enemy routing decisions add a strategic layer to movement |
| **Mastery (Challenge)** | Enemy types and placements scale the challenge ceiling |
| **Creativity (Discovery)** | Enemy-environment interactions reward experimentation |
| **Creativity (Design)** | Multiple approach vectors let players express personal style |
| **Immersion (Fantasy)** | Enemies deepen the tower's identity as a living, hostile place |

---

## Alignment with Game Pillars

### Pillar 1: Movement is Joy

> *The simple act of moving through the world must feel so good that traversal
> itself is its own reward.*

**Combat alignment**: Combat must never interrupt movement. It must never
require the player to stop, wait, or enter a separate mode. Every combat
interaction is a movement interaction first. The verbs are the same. The
feedback loop is the same. The joy of chaining wall-run → grapple → dash does
not change when an enemy is present — it gains an additional payoff layer.

**Design commitments**:
- No "attack button" — movement verbs are the only verbs.
- Neutralizing an enemy must preserve or increase the player's momentum. The
  design target is **net-positive momentum**: exiting a neutralization faster
  than you entered it.
- Enemies must be neutralizable in motion. The player should never need to stop
  moving to deal with a threat.
- Enemy density is capped at 3 per chunk so the player is never overwhelmed into
  forced combat. Bypass must always remain a viable option.

**Risk if violated**: Combat that stops or slows the player breaks the core
promise of the game. Players who came for movement will resent being forced to
fight. This is the highest-risk aspect of adding combat to VERTIGO, and the
primary reason the platformer concept originally excluded it.

### Pillar 2: Discoverable Depth

> *Every level contains layers that reward curiosity, from surface collectibles
> to hidden areas that transform how you see the world.*

**Combat alignment**: Enemies add a new layer of discoverable depth. They are
not just threats — they are **systemic tools** that interact with the
environment in discoverable ways. A curious player learns that a Charger's rush
can break weakened walls, revealing hidden areas. A Drone's scan beam briefly
illuminates invisible platforms. These interactions are never tutorialized —
they are discovered through experimentation, rewarding the Explorer player type.

**Design commitments**:
- Each enemy type has at least one **hidden environmental interaction** that is
  not explained to the player — it must be discovered.
- Enemy placements in early biomes are "safe" (easy to bypass, simple behaviors)
  so the player has room to experiment without pressure.
- Environmental clues hint at enemy-environment interactions (cracked walls near
  Chargers, faint shimmer where Drone beams pass).
- Hidden areas accessible only through enemy manipulation are marked subtly so
  observant players notice them before knowing how to reach them.

**Risk if violated**: If enemies are just obstacles with no systemic depth, they
become set dressing that adds nothing to the discovery layer. Worse, if enemies
are placed without environmental interaction potential, they actively reduce the
sense of depth by occupying space that could have held a secret.

### Pillar 3: Player-First Storytelling

> *The narrative emerges from what the player does, not from what the game tells
> them — your journey, not ours.*

**Combat alignment**: Enemies contribute to player-first storytelling by making
the tower feel **alive and reactive**. The presence of defenses implies a
history — someone or something built them. The player's relationship with these
defenses (do they fight? flee? exploit?) becomes part of their personal
narrative. The tower isn't just a static obstacle course; it's a place with a
past, and the enemies are the fragments of that past.

**Design commitments**:
- No enemy has a name, health bar, or explicit lore. What enemies *are* is
  conveyed through their visual design, behavior, and placement — never through
  text or dialogue.
- Enemy types change across biomes, reflecting the tower's different "eras" or
  zones. Foundry enemies are industrial and mechanical; Void enemies are
  abstract and reality-bending. This environmental progression tells a story
  without words.
- The player's choice of how to interact with enemies (bypass, neutralize,
  exploit) is never judged or scored differently. The game does not tell the
  player what kind of person they are — it lets them discover that through their
  own behavior.
- Enemy encounters never use scripted sequences, quick-time events, or forced
  combat arenas. Every enemy interaction emerges from the player's movement
  through the space.

**Risk if violated**: If enemies come with exposition, bestiary entries, or
moral framing ("these are the evil tower guardians"), they undermine the
player-first storytelling pillar. The player should form their own
interpretation of what the enemies are and what fighting (or not fighting) them
means. The narrative belongs to the player.

---

## Enemy Archetypes (Preliminary Sketch)

These are directional sketches, not final designs. Full enemy GDDs would follow
in separate documents.

| Archetype | Behavior | Movement Interaction | Environmental Secret | Biome Debut |
| --------- | -------- | -------------------- | -------------------- | ----------- |
| **Sentry** | Stationary; pulses a slow energy wave in a fixed direction. Wave can be dashed through (i-frames) or wall-run over. | Teaches dash-through and jump-over. Simplest threat. | Sentry waves briefly reveal hidden platforms when they pass over them. | Foundry |
| **Charger** | Patrols a horizontal path; on detecting the player, charges in a straight line. Can be baited, slide-ducked, or wall-run around. | Teaches baiting and slide timing. A charging Charger breaks weakened walls. | Charger's charge breaks cracked walls, opening hidden areas. | Foundry |
| **Drone** | Floats in a patrol pattern; projects a scanning cone. If the cone touches the player, the Drone emits a slowing pulse. Can be grappled and pulled. | Teaches grapple-as-offense. A grappled Drone can be swung into other enemies or used as a temporary anchor point. | Drone scan beams reveal invisible platforms while active. | Aqueduct |
| **Tether** | Stationary; projects an energy tether between itself and a partner Tether. Passing through the tether slows the player. Tethers can be broken by dashing through either anchor. | Teaches precision dash targeting. Broken tethers release a brief speed boost. | Tethers sometimes connect to hidden areas — following the tether line reveals the path. | Aqueduct |
| **Shard** | A cluster of crystalline fragments that orbit a central point. Individual shards can be dashed through; the central core requires a grapple-pull to disperse. | Teaches multi-target prioritization at speed. Dispersed shards become temporary grapple points. | Dispersed shard clusters leave behind a crystallized path that can be wall-run for a brief window. | Spire |
| **Echo** | A ghostly double of the player that mirrors their movements with a 1-second delay. Contact slows the player. Can only be neutralized by outrunning it (maintaining speed above a threshold for 3 seconds). | Teaches speed maintenance. Turns the player's own movement into the threat — the Echo is only dangerous if you hesitate. | An Echo's delayed path reveals safe routes through spike traps or crumbling platforms. | Void |
