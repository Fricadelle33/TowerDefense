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
attack_pattern: ring-6        # references attack-patterns.md
requires_facing: false
targets: AoE                  # single | AoE | N (numeric cap)
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
~~~

## Market cards

### Tier 1 — Early game

### Tier 2 — Mid game

### Tier 3 — End game