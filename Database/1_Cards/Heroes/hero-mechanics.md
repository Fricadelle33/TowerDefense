# Hero Mechanics

## Hero progression

### Repel rewards
When an enemy is Repelled (Zeal reaches 0), rewards trigger immediately:
- Decisive sap player gains full XP, all others gain 1 XP (trickle)
- Well cards dropped by elites are immediately available
  to add to any hero's deck
- Buy energy rewards (if stated on enemy card) granted
  to the player who dealt the decisive sap

### Progression
- Spend XP to level up
- Unlock new skills at new level
- Resolve Burrow draw if leveling triggers access

---

## Player Archetypes — Meta

| Archetype      | Relies on                            | Key field     |
|:----------     |:----------                           |:----------    |
| Engine builder | Playing cards, combo chains          | `effect`      |
| Discard engine | on_discard chains, `free_plays: 0`   | `on_discard`  |
| Hybrid         | Mix of both                          | both          |
| Market runner  | Buy energy generation, X-cost cards  | `buy_energy`  |

---

## The Burrow

A face-down hero-specific deck. Cards are never visible until drawn.

### Accessing The Burrow
A player may access The Burrow when:
- A conditional card's `unlocks_on` condition is met, OR
- The player spends 4 buy energy to access the Burrow

### Draw procedure
1. Draw the top 2 cards from The Burrow
2. Choose 1 to keep — add it to your deck immediately
3. Return the other face-down to The Burrow
4. Shuffle The Burrow

### Design intent
- Face-down deck creates variance across playthroughs
- Draw-2-choose-1 softens bad luck without eliminating it
- Shuffle after return prevents tracking the rejected card

```yaml
the_burrow:
  access_cost: 4   # flat buy energy cost to draw 2, choose 1
  deck:
    - card:TBD
    - card:TBD
    - card:TBD
    - card:TBD
    - card:TBD
```
