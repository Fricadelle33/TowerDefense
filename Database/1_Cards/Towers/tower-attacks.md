# Attack Patterns

## Grid system
- **Type**: Hex grid, flat-top orientation
- **Tile size**: 25mm
- **Facing**: Towers with `requires_facing: true` use a yellow-edge hex tile to indicate direction

## Pattern library

---

```yaml
id: pattern:single-tile
icon: ⬡
name: Single Tile
requires_facing: false 
tile_coverage: 1 (per pattern)
description: Affects the targeted tile only.
use_cases: [high damage output, clearing swarms of summoners]
```

```yaml
id: pattern:ring
icon: ◈
name: Ring-6
requires_facing: false
tile_coverage: 6
description: Affects all 6 adjacent hex tiles simultaneously. Omnidirectional.
use_cases: [poison aura, slow field, buff zone]
```

---

```yaml
id: pattern:cone
icon: ▲
name: Cone
requires_facing: true
tile_coverage: 3
description: Affects 3 tiles in the tower's facing direction. Rotatable via yellow-edge tile.
use_cases: [directional damage, knockback, fire breath]
```

---

```yaml
id: pattern:line
icon: ━
name: Line
requires_facing: true
tile_coverage: 3
description: Pierces through tiles in a straight line (up to 3 tiles deep).
use_cases: [piercing shot, chain lightning, beam]
```

---

```yaml
id: pattern:diagonal
icon: ✦
name: Diagonal
requires_facing: false
tile_coverage: 3
description: Hits 2nd-ring tiles in alternating directions, skipping adjacent tiles.
use_cases: [ricochet, crossfire, spread shot]
```

---

```yaml
id: pattern:aura
icon: ◉
name: Aura
requires_facing: false
tile_coverage: 1
description: Affects the tower's own tile. Enemies passing through trigger the effect.
use_cases: [trap, mine, ground effect]
```

---

```yaml
id: pattern:cross
icon: ⊕
name: Cross
requires_facing: false
tile_coverage: 4
description: Affects the 4 orthogonal adjacent tiles only (N/S/E/W on hex grid).
use_cases: [splash, shockwave, repel]
```

## Tower card integration

Towers reference a pattern via its `id` field:

```yaml
name: Venomous Fern
type: tower
attack_pattern: pattern:ring
requires_facing: false
priority: first
effect: Enemies on affected tiles take 1 poison counter per turn.
```

## Priority field values

| Value      | Targets                              |
| :--------- | :----------------------------------- |
| `first`    | Furthest along the path              |
| `last`     | Closest to spawn                     |
| `strongest`| Highest current Zeal                 |
| `weakest`  | Lowest current Zeal                 |
| `fastest`  | Highest speed stat                   |
| `tagged`   | Specific enemy tag (defined on card) |

Priority defines the tower's **default facing direction**. Players may override at placement.
