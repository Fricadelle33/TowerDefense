# Playmat

The global board is made of four mats, printed with hex tiles.

~~~yaml
grid:
  type: hex
  orientation: flat-top
  tile_size_mm: 25
~~~

~~~yaml
name: Bayou Depths
side: A
coordinates: [0, 0]
quadrant:Q1A
terrain: [swamp, water]
passive: Heroes with [water] element gain +1 combo at turn start
entry_points: [north, west]
exit_points: [east]
scenario_tags: [humid, toxic]
~~~

~~~yaml
quadrant:Q1B
side: B
coordinates: [0, 0]
~~~

~~~yaml
side: A
coordinates: [1, 0]
~~~

~~~yaml
side: B
coordinates: [1, 0]
~~~

~~~yaml
side: A
coordinates: [0, 1]
~~~

~~~yaml
side: B
coordinates: [0, 1]
~~~

~~~yaml
side: A
coordinates: [1, 1]
~~~

~~~yaml
side: B
coordinates: [1, 1]
~~~