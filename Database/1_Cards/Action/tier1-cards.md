~~~yaml
name: Swamp Gas
type: action
clan: hero
hero: croc
element: water
cost: 2
tags: [combo, poison]
tier: 1
attack_pattern: null
effect: Deal 3 damage. Apply 1 poison to all ring-6 tiles.
on_discard: Generate 1 buy energy. If combo ≥ 2 → apply 1 poison to nearest enemy
status_triggers:
  poisoned: "+6 damage"
  slowed: "+1 push"
  burning: "lose 1 armor permanently"
~~~

~~~yaml
effect: Reveal the top card of your deck. If it shares your element, draw it.
effect: Reveal your hand. For each water card revealed, deal 1 damage.
~~~