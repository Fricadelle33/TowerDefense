🪙🌀

~~~yaml
# Starting deck is low resource, unlocking the burrow is key for Croc
name: burrow-1
type: action
element: water
tags: [ ] # ==ToDo== Remove ?
cost: 4
targets: single          # single | AoE | chain
target_filter: all       # all | ground | aerial
effect: None
on_discard: >
  2🪙. If 🌀≥3 → Generate +2🪙
~~~

~~~yaml
name: From the den
type: action
element: none
tags: [ ]
cost: 4
effect: >
  If Barrier = 0 → Barrier 1.
on_discard: >
  Generate 2🪙.        
~~~

~~~yaml
name: Poise of the Gator
type: action
element: water
tags: [ ]
cost: 5
targets: single             
target_filter: all
effect: >
  If an enemy has 8 stacks of poison → Repel.
  (Bosses & elites are immune.)
~~~


~~~yaml
name: Creature from the swamp (+)
type: action
element: water
tags: [ ]
cost: 6
targets: AoE             
target_filter: all
effect: >
  Push 1 all enemies on target tile.
  If destination tile is occupied → Poison 1🌀 pushed enemies.
buy_energy: 0            
on-reveal: Remove Creature from the swamp from your deck.
meta: Control the enemy advance on and poison
~~~

~~~yaml
name: Tsunami Wave
type: action
element: water
tags: [ ]
cost: 8
targets: AoE
target_filter: all
effect: >
  Purge 4
  Push 1🌀 all enemies on target tile.
status_triggers:
  poison: Sap 1🌀. Cure all poison.
meta: THE card for Croc. Needs combo multipliers to work. 
~~~

~~~yaml
effect: >
  If you discarded ≥3 cards this turn → +1🌀.
~~~

