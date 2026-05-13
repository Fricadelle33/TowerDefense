# Hero: Croc O'Dill

~~~yaml
name: Croc O'Dill
element: water
difficulty: 2         # scale 1-5

lore: >
  An Irish-born crocodile with a sharp wit and sharper teeth.
  Croc O'Dill patrols the river networks of the Atlantic coast,
  defending the salmon tribe from upstream industrial poisoning.
  He fights dirty — and loves every second of it.

meta: >
  Croc O'Dill is a discard-engine hero who generates value through
  churn rather than raw power. He can cycle his hand aggressively
  without spending play energy, setting up devastating water combos
  mid-deck. Best paired with a damage dealer who can capitalize on
  the poison stacks he applies.

  Playstyle example:
  Discard discard discard → no combo movement, pure economy
  Play water card 1       → combo 1, element E = water
  Play water card 2       → combo 2
  Play water card 3       → combo 3
  Play tower (water)      → combo 4
  → Effect output = 4 × totem bonus → massive poison burst

tags:
  - water
  - carnivorous
  - discard-engine

free_plays: 3

skills:
  - name: Swamp Breath
    type: passive
    unlock_at_level: 1
    effect: TBD

  - name: Tampa Roll
    type: active
    unlock_at_level: 2
    cooldown: once_per_wave
    effect: TBD

  - name: Unmatched
    type: active
    unlock_at_level: 3
    cooldown: once_per_game
    effect: >
      All players simultaneously reveal 1 card from their hand.
      If N distinct elements are represented (N = player count), 
      Poison 3🌀.
      Target chosen by the triggering player.
      Revealed cards remain in hand.

starting_deck: file:hero-croc-cards.md

the_burrow:
  access_cost: 4 # flat buy energy cost to draw 2, choose 1 ==ToDo==
  deck: refer to file:hero-croc-burrow.md

campaign_additions: []

# XP
xp: 0                     # current XP
level: 1                  # current level
xp_to_next_level:
  2: 5
  3: 12

xp_modifier:
  on_ally_repel: +2 XP    # gains 2 extra XP when a teammate deals the decisive sap
  on_self_repel: +0 XP    # no bonus for own repels — support, not DPS
~~~