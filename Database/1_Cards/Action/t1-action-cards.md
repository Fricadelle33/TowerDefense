~~~yaml
name: Swamp Gas
type: action
element: water
tier: 1
cost: 2
tags: [combo, poison]
targets: single          # single | AoE | chain
target_filter: all       # all | ground | aerial
effect: Sap 3.
buy_energy: 0🪙          # buy energy generated when played
on_discard: >
  1🪙 extra.
  If combo ≥ 2 → Poison 1 nearest enemy.
status_triggers:
  poisoned: Sap 6 instead
  burning: Sap 5 and Push 1
loop-risk: false
~~~

~~~yaml
effect: Reveal the top card of your deck. If it shares your element, draw it.
effect: Reveal your hand. For each water card revealed, deal 1 damage.
~~~