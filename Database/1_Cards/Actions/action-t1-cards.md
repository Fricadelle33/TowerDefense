# T1 Cards

~~~yaml
name: Swamp Gas
type: action
element: water
tier: 1
cost: 2
tags: [combo, poison]
target_type: single
target_filter: all  
effect: Sap 3.
buy_energy: 1 
on_discard: >
  1🪙 extra.
  If combo ≥ 2 → Poison 1 nearest enemy.
status_triggers:
  poisoned: Sap 6 instead
  burning: Sap 5 and Push 1
~~~
