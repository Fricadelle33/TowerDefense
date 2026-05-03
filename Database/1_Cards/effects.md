# Effects and Statuses

## Player-applicable statuses

```yaml
poisoned:
  effect: >
    At start of enemy turn: lose Zeal equal to current stack count,
    then reduce stack count by 1. Expires at 0 stacks.
  stacks: yes
  armor_piercing: yes
  duration: equals stack count in turns
  cured_by: TBD
  zeal_curve: "3 stacks → 3+2+1 = 6 total Zeal sapped over 3 turns"
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
    burning: shatter — remove frozen, sap 2× Zeal on hit

thawed:
  effect: Vulnerable — sensitive to TBD (electricity candidate)
  stacks: no
  duration: 1 turn
  transitions_to: none
  note: vulnerability window for future element interaction

burning:
  effect: Lose 1 Zeal at start of turn
  armor_piercing: no
  stacks: no
  duration: 1 turn — extinguishes unless reapplied
  propagation: spreads to floor(fire icons played / 3) adjacent tiles
  note: >
    Short duration forces players to focus on burning enemies
    to maximize the Zeal-sap window and chain propagation
  status_triggers:
    frozen: shatter — remove frozen, sap 2× Zeal on hit
    poisoned: no interaction
```

---

## Enemy-specific statuses

```yaml
emboldened:
  effect: TBD — suggestion: +2 speed, +1 Zeal-sap on attack
  stacks: no
  triggered_by:
    - zeal ≤ 25% of max zeal
    - adjacent enemy is Repelled this turn
  note: >
    Repelling an enemy carelessly can embolden its neighbors.
    Players must consider repel order carefully.

thriving:
  effect: TBD — suggestion: regenerate 2 Zeal per turn
  stacks: TBD
  triggered_by: TBD
  note: >
    Double meaning intentional — a Thriving enemy is a corporation
    doing well. Fits the industrial lore perfectly.

corrupted:
  effect: >
    Gains 1 Thriving stack for each poison stack applied.
    Thriving stacks increase speed and Zeal-sap on attack.
  stacks: yes — via thriving
  triggered_by: poisoned status applied by any player
  note: >
    Fertilizer-fed enemy — poison intended to weaken instead
    empowers. Direct counter to poison-specialist heroes.
    Forces team coordination when revealed.
  status_triggers:
    poisoned: gain 1 thriving stack instead of losing Zeal

emboldened:
  effect: Gain N Zeal at end of turn if no Sap was applied this turn.
  stacks: no
  triggered_by:
    - zeal ≤ 25% of max zeal
    - adjacent enemy is Repelled this turn
  note: >
    Forces players to maintain constant pressure.
    A single Sap of any amount negates the Zeal gain entirely.
    Ignoring an Emboldened enemy is always a losing trade.
```

