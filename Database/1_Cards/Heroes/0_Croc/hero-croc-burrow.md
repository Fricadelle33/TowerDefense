# Croc Burrow

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
element: earth
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
  If you applied ≥8 Poison stacks this turn → Repel 1.
~~~

~~~yaml
name: Gator-Aid
type: action
element: water
cost: 3
on_discard: >
  Purge 1. Draw 1.
meta: A free water card for the combo. Or to cycle your deck.
~~~

~~~yaml
name: Entangled
type: action
element: leaves
cost: 3
target_type: single
target_filter: all
effect:
  Seal Poison.
on_discard:
  2🪙
meta: Preserve poison stacks to use poison damage
~~~

~~~yaml
name: Creature from the swamp (+)
type: action
element: water
cost: 5
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
cost: 6
target_type: AoE
target_filter: all
effect: 
  Purge 3. Push 2🌀. 
status_triggers:
  poisoned:
    also Sap 1🌀. Remove Poison.
meta: THE card for Croc. Get rid of your hand to launch a powerful combo Needs combo totems to work. 
~~~
