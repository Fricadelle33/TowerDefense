# Tower placement

## During your turn

A tower card played from hand is held in your **play zone**
for the duration of your turn. It sets or matches the combo
element for this turn. It does not occupy a hex tile until
end-of-turn placement.

### End-of-turn placement phase

After purging and drawing, place all towers from your play zone
onto the board. Placement is free but subject to:

## Shared footprint

All heroes share a single footprint pool defined on the scenario card.
The combined cost of all towers on the board cannot exceed the pool.

```yaml
footprint:
  shared_pool: 15
```

Footprint is scenario-wide and persistent — towers remain
on the board across waves unless Silenced by a Ravaged quadrant.
Some cards and totems may raise the shared pool permanently or temporarily.

## Placement rules

- Towers must be placed on a hex tile on an active (non-Ravaged) quadrant
- Towers may not be placed on path tiles occupied by an enemy meeple
- Towers with `requires_facing: true` must declare facing on placement
- Terrain affinity applies automatically based on the quadrant's terrain

## Terrain affinity

Towers and enemies may declare `terrain_affinity` triggers.
These resolve identically to `status_triggers` — same syntax,
same resolution order.

```yaml
terrain_affinity:
  mountains: +2 to all effects
  jungle: -2 to all effects
```

The mat defines the active terrain. Players read it once at setup.
No mid-game chart lookups required.

## At-capacity swap

If placing a tower would exceed the shared footprint pool, you may **Banish**
one or more towers currently on the board to free their footprint costs.

- Choose any towers on the board — they are removed from the game for the remainder of the scenario
- Their combined footprint cost is immediately freed
- You may Banish as many towers as needed to make room for the new one
- Banished towers are not discarded — they do not return to any deck this scenario

Swapping is a committed decision. Banished towers are gone until the next scenario.

## Facing

Facing may be changed freely at the start of any player turn at no cost.
