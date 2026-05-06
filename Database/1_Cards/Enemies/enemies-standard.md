# Standard Enemy Cards

## Card template

```yaml
name: Oil leak
type: standard                # standard | elite | boss
difficulty_rating: 3          # back office — informs scenario design and rewards

zeal: 12
speed: 2                      # tiles moved per enemy turn
shield: 3                     # absorbs Sap before Zeal is affected
flying: false

path_preference: northbound   # northbound | southbound | eastbound | westbound

on_spawn: Summon 1            # triggered once when enemy enters the path

on_turn: Erode 1              # triggered every enemy turn (step 1 of turn order)

on_shield_break:              # triggered when shield reaches 0
  if_tower: Silence 2
  if_hero: Erode 1

on_reach_exit: Erode 3        # triggered when enemy reaches path exit

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

# Rewards for standard enemies are written in the rules
```

## All cards

```yaml
name: Oil Rat
type: standard                
difficulty_rating: 1          
zeal: 12
speed: 2                      
shield: 0 

path_preference: northbound 

on_turn: Erode 1

on_reach_exit: Erode 3

status_triggers:
  burning: Burning spreads to enemies on adjacent path tiles

terrain_affinity:
  jungle: Burning -> Erode +1

reward:
  xp: 3
  buy_energy: 2
```
