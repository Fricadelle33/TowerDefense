# Action Cards

## template

~~~yaml
name: Swamp Gas+
type: action
element: water
tier: 2
cost: 2
tags: [combo, poison]
targets: single          # single | AoE | chain
target_filter: all       # all | ground | aerial
effect: Purge Swamp Gas from your hand. Sap 3.
buy_energy: 1            # buy energy generated when played
on_discard: >
  1🪙 extra.
  If combo ≥ 2 → Poison 1 nearest enemy.
status_triggers:
  poisoned: Sap 6 instead
  burning: Sap 5 and Push 1
loop-risk: false
~~~

## Market cards

### Tier 1 — Early game

### Tier 2 — Mid game

### Tier 3 — End game
