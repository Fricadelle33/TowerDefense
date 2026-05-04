# Elite and Boss Enemies

---

## Elite card template

```yaml
name: Oil Baron
type: elite                   # standard | elite | boss
difficulty_rating: 3          # back office — informs scenario design and rewards
zeal: 12
speed: 2                      # tiles moved per enemy turn
shield: 3                     # absorbs Sap before Zeal is affected

path_preference: northbound   # northbound | southbound | eastbound | westbound

on_shield_break:
  if_tower: Silence 2
  if_hero: Erode 1

effect: Summon 1.

per_turn:
  effect: Erode 1             # omit if no per-turn effect

status_triggers:
  poisoned: Sap 6 instead
  burning: Lose 1 shield permanently
  emboldened: Embolden 2
  thriving: Restore 2 Zeal per turn
  corrupted: Gain 1 thriving stack instead of losing Zeal

terrain_affinity:
  jungle: stealth — cannot be targeted by cone or line towers
  plains: -1 speed
  mountains: +1 shield

reward:
  xp: 3
  buy_energy: 2🪙
  well_card: fairy_well:N     # omit for standard enemies
```

---

## Boss card template

Bosses are scenario-specific. One boss per scenario, placed at the bottom of the
final wave deck. Repelling the boss is required to complete the scenario.

```yaml
name: The Conglomerate
type: boss
scenario: scenario:slug       # the scenario this boss belongs to
difficulty_rating: 5

zeal: 30
speed: 1
shield: 5

path_preference: northbound

# Bosses enter from the wave deck like elites, but are always last.
# Their meeple is visually distinct (larger or coloured differently).

on_shield_break:
  effect: Bury totem:any      # group chooses which totem is buried

# Phase triggers — fire once when Zeal crosses the threshold (not repeatable)
phases:
  - at_zeal: 20               # triggers when Zeal drops to 20 or below
    effect: Summon 2. Embolden 2 all enemies on path.
  - at_zeal: 10               # triggers when Zeal drops to 10 or below
    effect: >
      Bury totem:any. Ravage 1.
      All towers on Q1 are Silenced for 2 turns.

per_turn:
  effect: Erode 1

status_triggers:
  poisoned: immune            # bosses may be immune to specific statuses
  burning: Lose 1 shield permanently
  emboldened: Embolden 3
  thriving: Restore 3 Zeal per turn
  corrupted: Gain 2 thriving stacks instead of losing Zeal

terrain_affinity:
  jungle: stealth — cannot be targeted by cone or line towers
  mountains: +2 shield

# Win condition — repelling the boss satisfies the scenario win condition
win_condition: repel

reward:
  xp: 5
  # Boss reward is defined on the scenario card, not here.
  # No well_card — boss reward supersedes it.
```

### Boss design rules
- One boss per scenario, always the last card in the final wave deck
- `phases` trigger once only — crossing the threshold a second time does nothing
- `Bury` is exclusive to bosses — elites can only Silence totems
- Boss repel is a required win condition; scenarios may add further objectives
- Boss has no `well_card` reward — its repel reward is defined on the scenario card
