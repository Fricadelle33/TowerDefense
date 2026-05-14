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

A face-down hero-specific deck of powerful cards.

### Access condition
- A conditional card's `unlocks_on` condition is met, OR
— A hero may access the Burrow once per wave, only on a turn
where their draw deck is empty.

### Draw procedure
1. Reveal the top 2 cards from the Burrow
2. Choose 1 — pay its buy energy cost immediately
3. Add the chosen card to your hand or discard pile
4. Return the unchosen card face-down to the top of the Burrow
5. If you cannot afford either card:
   - Return both face-down to the top of the Burrow
   - You now know what to expect next access

The Burrow is never reshuffled after game setup.
Order is permanent — what you saw is what you'll see next time.

### Design intent
- Face-down deck creates variance across playthroughs
- Draw-2-choose-1 softens bad luck without eliminating it
- Empty deck gate rewards deck-thinning and cycling builds
- Once per wave prevents spam regardless of hero meta
- Individual card costs allow fine-grained power tuning per card

Each burrow is defined in file:hero-{HERO}-burrow.md

---

## Hero card template

```yaml
name: slug
element: water
difficulty: 2           # 1-5
lore: >
  One paragraph.
meta: >
  How to play this hero.
tags: [water, discard-engine]
free_plays: 3
xp: 0
level: 1
xp_to_next_level:
  2: 5
  3: 12
xp_modifier:
  on_ally_repel: +2      # support heroes
  on_self_repel: +0
skills:
  - name: Skill Name
    type: passive         # passive | active | hero_totem
    unlock_at_level: 1
    effect: TBD
  - name: Skill Name
    type: active
    unlock_at_level: 2
    cooldown: once_per_wave
    effect: TBD
  - name: Skill Name
    type: active
    unlock_at_level: 3
    cooldown: once_per_game
    effect: TBD
starting_deck:
  - card:slug
the_burrow:
  deck:
    - card: card:slug
      cost: 4
    - card: card:slug
      cost: 6
campaign_additions: []
starting_totem: null
```

> The Burrow IS the hero market — there is no `hero_market` field.
> Each Burrow card has its own individual cost.
> Burrow access requires once-per-wave + empty draw deck (see mechanics).