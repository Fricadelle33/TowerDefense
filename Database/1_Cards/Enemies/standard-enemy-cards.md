# Standard Enemy Cards

#### Card template

~~~yaml
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

effect: Summon 1.             # active effect when entering a tile or per turn — TBD

status_triggers:
  poisoned: Sap 6 instead
  burning: lose 1 shield permanently
  emboldened: Embolden 2
  thriving: Restore 2 Zeal per turn
  corrupted: gain 1 thriving stack instead of losing Zeal

reward:
  xp: 3
  buy_energy: 2🪙
  well_card: card:TBD         # omit for standard enemies
~~~