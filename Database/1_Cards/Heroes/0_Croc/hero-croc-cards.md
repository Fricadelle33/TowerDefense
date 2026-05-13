# Croc starting deck

## Action cards

~~~yaml
name: No diggity
type: action
element: water
tags: [ ]
target_type: single
target_filter: all
effect: None
buy_energy: 0
on_discard: >
  3🪙
  Purge a card
meta: Main buying card. Expensive but rewarding.
~~~

~~~yaml
name: Creature from the swamp
type: action
element: water
tags: [ ]
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
element: none
tags: [ ]
target_type: single
target_filter: all
effect: >
  Sap 1.
status_triggers:
  poisoned: Poison 2 instead.
~~~

~~~yaml
name: Do a barrel roll
type: action
element: none
tags: [ ]
effect: >
<<<<<<< HEAD
  Protect 1.
=======
  Barrier 1.
>>>>>>> ab33289 (cards(design): created first hero deck and burrow)
status_triggers:
  poisoned: You can Poison 2 instead.
~~~

~~~yaml
name: Steam
type: action
element: water, air
tags: [ ]
target_type: AoE
target_filter: all
effect: >
  Slow 1.
  (All enemies on targeted tile)
status_triggers:
  burning: remove burning state.
meta: Dual-element card to vary the deck.
~~~

~~~yaml
name: Croc-a-mole
type: action
tags: [ ]
element: water
on_discard:
  Purge 1. Draw 1.
meta: A free water card for the combo. Or to cycle your deck.
~~~

~~~yaml
name: Lurking 
type: action
tags: [ ]
element: water
buy_energy: 2
effect: >
  If you discarded ≥3 cards this turn → +1🌀
on_discard:
  -1🌀
meta: The only other source of money with water element.
~~~

## Towers

~~~yaml
name: Venomous Fern
type: tower
element: water
cost: 4
terrain: [swamp, jungle]
tags: [poison, zone]
requires_facing: false
attack_pattern: pattern:ring  # references tower-attacks.md
target_type: AoE         
target_filter: ground
priority: first
status_triggers:
  poisoned: Poison -1
upgrade_condition: contract:green-thumb
levels:
  1:
    effect: Poison 1.
  2:
    effect: Poison 1🌀.
terrain_affinity: # ==ToDo== Not sure
  mountains: -2 to all effects
  plains: -2 to all effects
~~~

~~~yaml
name: Salmon tribe
type: tower
element: water
cost: 4
terrain: [swamp]
tags: [ ]
requires_facing: true
attack_pattern: pattern:line
target_type: per_tile         # 1 enemy per tile of the pattern 
target_filter: ground
status_triggers:
  poisoned: Poison -1         # Lower the poison ticks
upgrade_condition: Croc's burrow is empty
levels:
  1:
    effect: >
      Sap 1.
      On repel → re-activate any `on_discard` effect played this turn (once)
  2:
    effect: > 
      Sap 1🌀.
      On repel → re-activate any number of `on_discard` effects 
terrain_affinity: # ==ToDo== Not sure
  swamp: No additional effects.
  not-swamp: Salmon tribe is Silenced.
~~~