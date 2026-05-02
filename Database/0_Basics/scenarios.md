# Scenarios 

The scenarios are meant to be played in order. They were intended to provide an increasing difficulty throughout the campaign.

> ### ==ToDo==
> Enemy objectives, number of waves, difficulty scaling

#### Scenario objectives
Standard scenario:  Wight = shared HP pool, abstract, off-board
VIP scenario:       Wight = meeple on the path, has HP, 
                    moves along path (toward exit or away from enemies)
                    enemies prioritize targeting it

#### Scenario scoring 


#### Scenario template

~~~yaml
name: The First Flood
total_tiles: # Number of tiles composing the path
objectives: 
  objective_1: Survive
    scoring_1:
      - flawless: Survive with 90% or more land preserved
      - excellent: Survive with 80% or more land preserved
      - good: Survive with 70% or less more preserved
      - cursed: Survive with strictly less than 70% land preserved
scenario_type: [standard, VIP] # TBD
reward:
  - flawless: card:river-kings-blessing
  - excellent:
  - good:
  - cursed:
quadrants: [Q1, Q3]
orientation: [Q1-north, Q3-south]
connection: Q1-south → Q3-north
paths:
  - start: Q1-entry-west
  - end: Q3-exit-east
  - splits: false
  - tile-sequence: [hex-tile:straight, hex-tile:y] # Full programmatic path definition
difficulty: 1
waves: 3
wight:
  type: vip
  name: The Dryad
  hp: 8
  speed: 1              # advances 1 tile per round automatically
  position: hex:entry   # starting position on path
  enemy_priority: true  # enemies target Wight over objectives
  lose_condition: wight:hp-reaches-0
~~~

### Scenario : Introduction

~~~yaml
name: introduction
~~~

