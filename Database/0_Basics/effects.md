# Effects and Statuses

## General rules on card effects

Card effects must be applied fully, in up-to-bottom, left-to-right order.
X cards must use all X resources available, but X can be zero.

## Player-applicable statuses

```yaml
poisoned:
  effect: >
    After tower effects fire: lose 1 Zeal, stack count decreases by 1.
    Expires when stack count reaches 0.
  stacks: yes
  tick_zeal_loss: 1         # always flat 1, regardless of stack count
  duration: equals stack count in turns
  zeal_curve: "5 stacks → 1 Zeal lost per turn × 5 turns = 5 total"
  primary_value: >
    Duration of poisoned state for status_trigger exploitation,
    not raw Zeal damage.
  status_triggers:
    burning: no interaction
    frozen: no interaction

slowed:
  effect: Reduce speed by N this turn. If speed reaches 0, enemy does not move.
  ignore_shield: yes
  stacks: no
  duration: 1 turn
  note: Slow 3 reduces speed by 3. Does not transition to thawed.

frozen:
  effect: >
    Reduce speed to 0, regardless of initial value. Enemy does not move this turn.
    Frozen = Slow equal to the enemy's full speed stat.
  ignore_shield: yes
  transitions_to: thawed
  stacks: no
  duration: 1 turn
  status_triggers:
    burning: shatter — remove frozen, sap 2× Zeal on hit

thawed:
  effect: Vulnerable. Action cards may check `if thawed` to trigger bonus effects.
  stacks: no
  duration: 1 turn
  transitions_to: none

burning:
  effect: >
    After tower effects fire: lose 1 Zeal.
    Propagate to `floor(fire icons played / 3)` adjacent tiles
  ignore_shield: no
  stacks: no
  duration: 1 turn — extinguishes unless reapplied
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
thriving:
  effect: Gain 2 Zeal per turn
  stacks: no
  triggered_by: n/a
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
