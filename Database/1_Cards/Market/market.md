# Market

## Structure
- 6 cards visible simultaneously in a shared central zone
- One market deck per tier (3 decks total)
- Composition set during scenario setup based on player count

## Tiers
- Tier 1: available from wave 1
- Tier 2: unlocks when scenario-defined condition is met
- Tier 3: unlocks when scenario-defined condition is met

```yaml
# Example scenario market definition
market:
  tier_1_count: 12
  tier_2_count: 8
  tier_3_count: 6
  tier_2_unlocks_on: elite:first-elite-repelled
  tier_3_unlocks_on: wave:5
```

## Draft mechanics
- 6 cards always visible, drawn from the active tier deck
- When a card is bought: immediately replaced from the same tier deck
- When a tier deck is exhausted: slots remain empty until next tier unlocks
- Players may buy unlimited cards per turn (limited by buy energy only)

## Market cleanup — Dismiss
A player may dismiss their hand at any point during their turn.

- Forfeit all cards in hand simultaneously
- No `on_discard` effects trigger
- No play energy generated
- Gain +3 buy energy immediately
- Market refreshes (new draft pool drawn)

Dismiss is a bold move — it sacrifices tempo entirely for 
market access and buy power.

## Market composition by player count
TBD — to be defined once card set size is known


### Market card template

```yaml
name: slug
type: action
element: water          # water | leaves | ground | air  — or array [water, air] for dual-element
tier: 1                 # 1 | 2 | 3
cost: 2                 # buy energy cost to acquire from market
tags: [combo, poison]
target_type: single     # single | AoE — multiplicity per affected tile
target_filter: all      # all | ground | aerial | standard
effect: Sap 3.
on_discard: 1🪙. If combo ≥ 2 → Poison 1 nearest enemy.
status_triggers:
  poisoned: Sap 6 instead
  burning: Sap 5 and Push 1
terrain_affinity:
  swamp: +1 Sap
loop-risk: false
```

> Action cards do NOT use `attack_pattern`. The effect text describes
> the spatial footprint. Patterns are tower-only.