# Standard Enemy Cards

#### Card template

~~~yaml
name: Oil Baron
difficulty_rating: 3
hp: 12
speed: 2
armor: 3
on_armor_break: current terrain gets ravaged
status_triggers:
  poisoned: "+6 damage"
  slowed: "+1 push"
  burning: "lose 1 armor permanently"
  blessed: "+2 to all effects this turn"    # buff example on enemy
  enraged: "+2 speed, +1 damage"            # buff on enemy (dangerous)
~~~