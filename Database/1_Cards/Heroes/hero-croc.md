# Hero 1

~~~yaml
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
  churn rather than raw power. With 3 free plays per turn, he can
  cycle his hand aggressively without spending play energy, setting
  up devastating water combos mid-deck. Best paired with a damage
  dealer who can capitalize on the poison stacks he applies.

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

  - name: Death Roll
    type: active
    unlock_at_level: 2
    cooldown: once_per_wave
    effect: TBD

  - name: Deathmatch
    type: active
    unlock_at_level: 3
    cooldown: once_per_game
    effect: >
      All players simultaneously reveal 1 card from their hand.
      If N distinct elements are represented (N = player count),
      one target mob suffers ×3 damage this turn.
      Target chosen by the triggering player.
      Revealed cards remain in hand.

starting_deck:
  - card:croc-a-mole
  - card:do-a-barrel-roll
  - card:creature-from-the-swamp
  - card:dilly-dallies
  - card:steam

hero_market:
  deck:
    - card:TBD
    - card:TBD
    - card:TBD
    - card:TBD
    - card:TBD
  draw: 2
  choose: 1
  shuffles: once_per_scenario

the_burrow:
  access_cost: 4 # flat buy energy cost to draw 2, choose 1 ==ToDo==
  deck:
    - card:swamp-tactics
    - card:river-cunning
    - card:death-roll
    - card:apex-predator
    - card:TBD

campaign_additions: []

starting_totem: null
~~~