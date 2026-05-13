# Tower Cards

## template

~~~yaml
name: Venomous Fern
type: tower
element: water
tier: [1, 2]
cost: 4
terrain: [swamp, forest]
tags: [poison, zone]
requires_facing: false
attack_pattern: pattern:ring  # references tower-attacks.md
target_type: AoE              # single | AoE | N (numeric cap)
target_filter: ground         # ground | aerial | all
priority: first
status_triggers:
  poisoned: Poison 2 instead of Poison 1
upgrade_condition: contract:green-thumb
levels:
  1:
    effect: Poison 1 all enemies on affected tiles per turn.
  2:
    effect: Poison 2 all enemies on affected tiles per turn.
terrain_affinity:
  mountains: +2 to all effects
  jungle: -2 to all effects
  swamp: Poison 1 additional stack
~~~

## Market cards

### Tier 1 — Early game

### Tier 2 — Mid game

### Tier 3 — End game