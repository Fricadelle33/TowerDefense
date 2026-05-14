🪙🌀

~~~yaml
name: Beavers give a hand
type: action
element: water
cost: 4
on_discard: >
  2🪙. If 🌀≥3 → +2🪙
meta: Starting deck is low resource, unlocking the burrow is key for Croc
~~~

~~~yaml
name: From the den
type: action
element: ground
cost: 4
effect: >
  If no Barrier tokens → Barrier 2.
on_discard: >
  2🪙.        
~~~

~~~yaml
name: Poise of the Gator
type: action
element: water
cost: 5
target_type: single            
target_filter: standard
effect: >
  If target has ≥8 Poison stacks → Repel.
~~~

~~~yaml
name: Gator-Aid
type: action
element: water
cost: 3
on_discard:
  Purge 1. Draw 1.
meta: A free water card for the combo. Or to cycle your deck.
~~~

~~~yaml
name: Entangled
type: action
element: leaves
target_type: single
target_filter: all
effect: > # Intended prose — No canonical verb  
  Target enemy cannot lose or gain poison stacks
  until the end of the turn. (Existing Poison still ticks).
on_discard:
  2🪙
meta: Preserve poison stacks to use poison damage
~~~

~~~yaml
name: Creature from the swamp (+)
type: action
element: water
cost: 6
target_type: AoE             
target_filter: all
effect: >
  Push 1.
  If destination tile is occupied → Poison 1🌀. 
upgrade: card:creature-from-the-swamp
meta: Control the enemy advance on and poison
~~~

~~~yaml
name: Tsunami Wave
type: action
element: water
cost: 8
target_type: AoE
target_filter: all
effect: >
  Purge 4. Push 1🌀.
status_triggers:
  poisoned: Sap 1🌀. Remove Poison.
meta: THE card for Croc. Needs combo multipliers to work. 
~~~
