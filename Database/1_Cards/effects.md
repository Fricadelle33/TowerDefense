# statuses.md

## Player-applicable statuses

~~~yaml
poisoned:
  effect: >
    At start of enemy turn: lose hp equal to current stack count,
    then reduce stack count by 1. Expires at 0 stacks.
  stacks: yes
  armor_piercing: yes
  duration: equals stack count in turns
  cured_by: TBD
  damage_curve: "3 stacks → 3+2+1 = 6 total damage over 3 turns"
  status_triggers:
    burning: no interaction
    frozen: no interaction

frozen:
  effect: Cannot move this turn
  armor_piercing: yes
  stacks: no
  duration: 1 turn
  transitions_to: thawed
  status_triggers:
    burning: shatter — remove frozen, deal 2× damage on hit

thawed:
  effect: Vulnerable — sensitive to TBD (electricity candidate)
  stacks: no
  duration: 1 turn
  transitions_to: none
  note: vulnerability window for future element interaction

burning:
  effect: Lose 1 hp at start of turn
  armor_piercing: no
  stacks: no
  duration: 1 turn — extinguishes unless reapplied
  propagation: spreads to floor(fire icons played / 3) adjacent tiles
  note: >
    Short duration forces players to focus fire on burning enemies
    to maximize damage window and chain propagation
  status_triggers:
    frozen: shatter — remove frozen, deal 2× damage on hit
    poisoned: no interaction

## Enemy-specific statuses

enraged:
  effect: TBD — suggestion: +2 speed, +1 damage
  stacks: no
  triggered_by:
    - hp ≤ 25% of max hp
    - adjacent mob dies this turn
  note: >
    Killing a mob carelessly can enrage its neighbors.
    Players must consider kill order carefully.

thriving:
  effect: TBD — suggestion: regenerate 2 hp per turn
  stacks: TBD
  triggered_by: TBD
  note: >
    Double meaning intentional — a Thriving enemy is a corporation
    doing well. Fits the industrial lore.

corrupted:
  effect: >
    Gains 1 Thriving stack for each poison stack applied.
    Thriving stacks increase speed and damage.
  stacks: yes — via thriving
  triggered_by: poisoned status applied by any player
  note: >
    Fertilizer-fed mob — poison intended to weaken instead
    empowers. Direct counter to poison-specialist heroes.
    Forces team coordination when revealed.
  status_triggers:
    poisoned: gain 1 thriving stack instead of taking damage
~~~