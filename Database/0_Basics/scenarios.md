# Scenarios

The scenarios are meant to be played in order. They were intended to
provide increasing difficulty throughout the campaign.

> ### ==ToDo==
> Enemy objectives, number of waves, difficulty scaling

---

## Scenario types

**Standard** — Wights represented as a shared land integrity pool,
tracked via desolation tokens per quadrant. Heroes defend them collectively.

**VIP** — one or more Wights represented as meeples on the path,
with individual land integrity and movement. Enemies prioritize targeting them.

---

## Land integrity tracking

Land integrity is tracked at the **quadrant level** using desolation tokens.

Each quadrant has a `resilience` value — the number of desolation tokens
it can absorb before becoming Ravaged. Global resilience reductions
(from Ravage effects) apply to all quadrants simultaneously.

```
Example: resilience per_quadrant = 5, global = 0
Q1: [ ][ ][ ][ ][ ]   → 0 desolation tokens, 5 remaining
Q2: [x][ ][ ][ ][ ]   → 1 desolation token,  4 remaining
Q3: [x][x][x][ ][ ]   → 3 desolation tokens, 2 remaining
Q4: [x][x][x][x][x]   → RAVAGED — all towers on Q4 permanently Silenced
```

When all active quadrants are Ravaged: **game over**.

---

## Scenario scoring

| Rating | Condition |
|:---|:---|
| Flawless | Survive with 90%+ land integrity preserved |
| Excellent | Survive with 80%+ land integrity preserved |
| Good | Survive with 70%+ land integrity preserved |
| Cursed | Survive with less than 70% land integrity preserved |

`land integrity preserved = total remaining resilience / total starting resilience × 100%`

---

## Scenario template

```yaml
name: The First Flood
scenario_type: standard     # standard | VIP
difficulty: 1               # 1-5, back office reference
total_tiles:                # number of hex tiles composing the path

# Land integrity
resilience:
  per_quadrant: 5           # default resilience for all quadrants
  Q1: 5                     # override per quadrant for asymmetric scenarios
  Q2: 5
  Q3: 5
  Q4: 5

# Objectives
objectives:
  objective_1: Survive

# Scoring
scoring:
  flawless: Survive with 90% or more land integrity preserved
  excellent: Survive with 80% or more land integrity preserved
  good:      Survive with 70% or more land integrity preserved
  cursed:    Survive with strictly less than 70% land integrity preserved

# Rewards
reward:
  flawless: card:river-kings-blessing
  excellent:
  good:
  cursed:

# Board layout
quadrants: [Q1, Q3]
orientation: [Q1-north, Q3-south]
connection: Q1-south → Q3-north

paths:
  - start: Q1-entry-west
  - end: Q3-exit-east
  - splits: false
  - tile-sequence: [hex-tile:straight, hex-tile:y]   # full programmatic path definition

# Market
market:
  tier_1_count: 12
  tier_2_count: 8
  tier_3_count: 6
  tier_2_unlocks_on: elite:first-elite-repelled
  tier_3_unlocks_on: wave:5

# Waves
waves: 3

# VIP-specific fields (omit for standard scenarios)
wight:
  type: vip
  name: The Dryad
  land_integrity: 8
  speed: 1                  # advances 1 tile per round automatically
  position: hex:entry       # starting position on path
  enemy_priority: true      # enemies target Wight over objectives
  lose_condition: wight:land-integrity-reaches-0
```

---

## Scenario: Introduction

```yaml
name: introduction
```
