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
effect: >
  Sap 1.
status_triggers:
  poisoned: Poison 2 instead.
~~~

~~~yaml
name: Do a barrel roll
type: action
element: water
target_type: single
target_filter: all
effect: >
  Barrier 1.
status_triggers:
  poisoned: Poison 2 instead.
~~~

~~~yaml
name: Steam
type: action
element: [water, air]
target_type: AoE
target_filter: all
effect: >
  Slow 1.
status_triggers:
  burning: Remove Burn.
meta: Dual-element card to vary the deck.
~~~

~~~yaml
name: Croconavirus
type: action
element: air
target_type: AoE
target_filter: aerial
effect: >
  Tick Poison.
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
# ==ToDo== Check / rewrite
name: Croc n' roll
type: action
element: ground
effect: > # claude: strict-validator override
  2🪙 (element:ground card only)
on_discard: # claude: strict-validator override
  Place this card on a player's play area. It counts towards their combo. Return this card end of turn.
meta: Money or coop :)
~~~

## Towers

~~~yaml
name: Venomous Fern
type: tower
element: air
cost: 4
terrain: [swamp, jungle]
tags: [poison, zone]
requires_facing: false
attack_pattern: pattern:ring  # references tower-attacks.md
target_type: AoE         
target_filter: ground
priority: first
status_triggers:
  poisoned: Remove 1 Poison.
upgrade_condition: contract:green-thumb
levels:
  1:
    effect: Poison 1.
  2:
    effect: Poison 1🌀.
terrain_affinity: 
  mountains: -2 to all effects # ==ToDo== Not sure
  plains: -2 to all effects # ==ToDo== Not sure
~~~

~~~yaml
name: Salmon tribe
type: tower
element: water
cost: 4
terrain: [swamp]
requires_facing: true
attack_pattern: pattern:line
target_type: per_tile                      # 1 enemy per tile of the pattern 
target_filter: ground
status_triggers:
  poisoned: Remove 1 Poison.
upgrade_condition: hero:croc-o-dill:burrow-empty
levels:
  1:
    effect: >
      Sap 1.
      On repel → Trigger any `on_discard` effect played this turn (once)
  2:
    effect: > 
      Sap 1🌀.
      On repel → Trigger any `on_discard` effect played this turn 
terrain_affinity: # ==ToDo== Not sure
  not-swamp: Salmon tribe cannot be played.
~~~