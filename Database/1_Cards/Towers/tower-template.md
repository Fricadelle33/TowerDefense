# Tower card template

```yaml
name: slug
type: tower
element: water
tier: [1, 2]
cost: 4
terrain: [swamp, forest]       # swamp | jungle | mountains | plains | none
tags: [poison, zone]
requires_facing: false
attack_pattern: pattern:ring   # pattern:single-tile | pattern:ring |
                               # pattern:cone | pattern:line | pattern:diagonal |
                               # pattern:aura | pattern:cross
target_type: AoE               # single | AoE | per_tile
target_filter: ground          # ground | aerial | standard
priority: first                # first | last | strongest | weakest | fastest | tagged
status_triggers:
  poisoned: Poison 2 instead of Poison 1
terrain_affinity:              # swamp | jungle | mountains | plains | none
  mountains: +2 to all effects
  jungle: -2 to all effects
upgrade_condition: contract:green-thumb
levels:
  1:
    effect: Poison 1 all enemies on affected tiles per turn.
  2:
    effect: Poison 2 all enemies on affected tiles per turn.
```

> Pattern definitions (in `tower-attacks.md`) carry `tile_coverage`
> (spatial footprint) and `requires_facing`. The card carries
> `target_type` (per-tile multiplicity) and `target_filter`.
