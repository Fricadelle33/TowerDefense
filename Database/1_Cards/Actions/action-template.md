# Action card template

```yaml
name: slug
type: action
element: water          # water | leaves | earth | air
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
loop-risk: false
```

> Action cards do NOT use `attack_pattern`. The effect text describes
> the spatial footprint. Patterns are tower-only.
