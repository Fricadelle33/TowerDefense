# Scenarios

The scenarios are meant to be played in order, providing
increasing difficulty throughout the campaign.

> ### ==ToDo==
> Enemy objectives, number of waves, difficulty scaling

## Scenario types

**Standard** — Wights represented as a shared land integrity pool,
abstract and off-board. Heroes defend them collectively.

**VIP** — one or more Wights represented as meeples on the path,
with individual land integrity and movement. Enemies prioritize
targeting them.

## Scenario scoring

TBD

## Scenario template

```yaml
name: The First Flood
total_tiles:          # Number of hex tiles composing the path
scenario_type: standard   # standard | VIP
difficulty: 1

objectives:
  objective_1: Survive
  scoring_1:
    flawless: Survive with 90% or more land integrity preserved
    excellent: Survive with 80% or more land integrity preserved
    good: Survive with 70% or more land integrity preserved
    cursed: Survive with strictly less than 70% land integrity preserved

reward:
  flawless: card:river-kings-blessing
  excellent:
  good:
  cursed:

market:
  tier_1_count: 12
  tier_2_count: 8
  tier_3_count: 6
  tier_2_unlocks_on: elite:first-elite-repelled
  tier_3_unlocks_on: wave:5

quadrants: [Q1, Q3]
orientation: [Q1-north, Q3-south]
connection: Q1-south → Q3-north

paths:
  - start: Q1-entry-west
  - end: Q3-exit-east
  - splits: false
  - tile-sequence: [hex-tile:straight, hex-tile:y]   # full programmatic path definition

waves: 3

# VIP-specific fields (omit for standard scenarios)
wight:
  type: vip
  name: The Dryad
  land_integrity: 8
  speed: 1                # advances 1 tile per round automatically
  position: hex:entry     # starting position on path
  enemy_priority: true    # enemies target Wight over other objectives
  lose_condition: wight:land-integrity-reaches-0
```

## Scenario: Introduction

```yaml
name: introduction
```
