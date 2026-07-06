# Croc starting deck

10 cards.

## Action cards

~~~yaml
name: No diggity
type: action
element: water
target_type: single
target_filter: all
effect: None
on_discard: >
  3🪙.
  Purge 1.
meta: Main buying card. Expensive but rewarding.
~~~

~~~yaml
name: Creature from the swamp
type: action
element: water
target_type: single
target_filter: all
effect: >
  Push 1.
  If destination tile is occupied → Poison 1🌀.
meta: Stack ticks of poison. But needs to build up the combo
~~~

~~~yaml
name: Crocodilly-dally
type: action
element: water
target_type: single
target_filter: all
effect:
  Sap 1.
  Poison 1 (different target).
~~~

~~~yaml
name: Do a barrel roll
type: action
element: water
effect: >
  Barrier 1.
  If quadrant has ≥3 desolation tokens, Barrier 2 instead.
~~~

~~~yaml
name: Steam
type: action
element: [water, air]
target_type: AoE
target_filter: all
effect:
  Slow 1.
status_triggers:
  burning: Also remove Burn.
meta: Dual-element card to vary the deck.
~~~

~~~yaml
name: Croconavirus
type: action
element: [water, air]
target_type: AoE
target_filter: all
effect:
  Tick Poison. Remove 1 Poison. 
meta: A powerful double poison
~~~

~~~yaml
name: Lurking
type: action
element: water
effect: >
  If you discarded ≥3 cards this turn → 🌀+1
on_discard:
  2🪙
meta: Money or combo... Your choice.
~~~

~~~yaml
name: Ice Croc Sandwich
type: action
element: water
cost: 4
target_type: ground
target_filter: standard
status_triggers:
  thawed: Tick Poison
  frozen: Seal Poison
on_discard: 1🪙
~~~

## Starting Towers

~~~yaml
name: Venomous Fern
type: tower
element: earth
cost: 4
terrain: [swamp, jungle]
tags: [poison, zone]
requires_facing: false
attack_pattern: pattern:ring  # references tower-attacks.md
target_type: AoE         
target_filter: ground
priority: first
status_triggers:
  poisoned: Sap 1 and Remove 1 Poison instead.
upgrade_condition: contract:green-thumb
levels:
  1:
    effect: Poison 1.
  2:
    effect: Poison 1🌀.
terrain_affinity: 
  mountains: 🌀-2
  plains: 🌀-2
meta: Early: convert poison to damage. Best for mid to late game.
~~~

~~~yaml
name: Salmon tribe
type: tower
element: water
cost: 4
terrain: [swamp]
requires_facing: true
attack_pattern: pattern:line
target_type: per_tile                      # 1 target per tile of the pattern 
target_filter: ground
upgrade_condition: burrow-empty            # Croc o' dill starting card: hero condition is implied
levels:
  1:
    effect: >
      Sap 1. Remove 1 Poison.
      On repel → Trigger any `on_discard` effect played this turn (once per turn)
  2:
    effect: > 
      Sap 2🌀. Remove 1🌀 Poison (down to 1 Poison minimum). 
      On repel → Trigger any `on_discard` effect played this turn (once per turn)
~~~
