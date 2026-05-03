# Enemy Movement

## Speed
Each enemy moves a number of hex tiles equal to their `speed` stat.
Movement is the **last step** of the enemy turn — enemies act before they move.

---

## Slow
**Slow N** — reduce enemy speed by N this turn.
If speed reaches 0 or below, the enemy does not move this turn.

> **Frozen** is Slow equal to the target's full speed stat.
> A speed-1 enemy hit by Slow 1 does not move this turn.
> Frozen transitions to Thawed after 1 turn.

---

## Path following
Enemies follow the hex tile path on the board.
At Y-intersections, enemies follow their `path_preference` field:

```yaml
path_preference: northbound   # northbound | southbound | eastbound | westbound
```

If preference conflicts with available paths, the enemy takes
the shortest route to the nearest objective.

---

## Enemy turn order
Resolved per enemy, sequentially from **furthest along path to closest**:

1. **Per-turn effects** — Erode N, Ravage N, Summon N, Embolden check
2. **Status ticks**
   - Poison: enemy loses Zeal equal to stack count, then stack count decreases by 1
   - Burning: enemy loses 1 Zeal, checks propagation to adjacent tiles
3. **Move** — advance speed tiles along the path
4. **Objective reached** — if enemy reaches exit this turn:
   - Trigger `on_reach_exit` effect (if any)
   - Apply `erode` value to the exit quadrant
   - Remove meeple from the board
   - **No repel rewards granted**

> Enemies that reach their objective are not Repelled.
> No XP, no Well cards, no 🪙. Letting enemies through is always a losing trade.

---

## Erode and Ravage

### Erode N — quadrant-based
Place N desolation tokens on the quadrant the enemy currently occupies.
If desolation tokens on that quadrant reach its resilience value,
that quadrant becomes **Ravaged**.

```yaml
name: Oil Baron
erode: 3    # places 3 desolation tokens on current quadrant on exit
```

### Ravage N — global
Reduce global resilience by N permanently.
All quadrants become N points closer to being Ravaged simultaneously.
Cannot be recovered within a scenario.

```yaml
name: The Conglomerate
on_reach_exit:
  ravage: 2   # reduces all quadrant resilience by 2
```

### Ravaged quadrant
When a quadrant's desolation tokens reach its resilience threshold:
- All towers on that quadrant are **permanently Silenced**
- The quadrant remains on the board — heroes can still play there
- No further desolation tokens are placed on a Ravaged quadrant

When **all active quadrants** are Ravaged: game over.

---

## Per-turn effects
Some enemies trigger effects every turn regardless of movement.
Resolved in step 1 of the enemy turn order.

```yaml
name: Drilling Rig
speed: 1
erode: 2        # on reaching objective
per_turn:
  effect: Erode 1   # places 1 desolation token on current quadrant every turn
```

Slow enemies with per-turn Erode are priority targets —
every turn of inaction costs land integrity.

---

## VIP Wight movement
In VIP scenarios, the Wight meeple moves at the **start of the enemy turn**,
before any enemy resolves their turn order.
Speed defined on the scenario card under `wight:speed`.

If an enemy occupies the same tile as the Wight after their move phase:
- They attack the Wight directly
- Erode its individual land integrity instead of the quadrant pool
- If Wight land integrity reaches 0: trigger VIP lose condition
