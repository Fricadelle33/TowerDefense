# Glossary

## Core vocabulary

### Zeal

An enemy's drive and organizational momentum. Replaces HP on all enemy cards. When Zeal reaches 0, the enemy is Repelled.

### Repel

The moment an enemy's Zeal reaches 0. The enemy meeple is removed from the path. Triggers repel rewards immediately. Can be a card effect.

#### Repel reward

Rewards granted instantly when an enemy is Repelled:

- XP awarded to the player who dealt the decisive sap
- Well cards dropped by elites, immediately available to add to any hero's deck
- Buy energy rewards stated on the enemy card

#### Land integrity

The Wights' shared integrity pool, tracked on the board.
When land integrity reaches 0, the land is ravaged and players lose.

---

## Card actions and verbs

```yaml
file: Database/1_Cards/effects-vocabulary.md
```

### Usage of Reveal

- Used by active skills and specific card effects
- All players may reveal simultaneously when an effect requires it
- Revealing does not count as a discard, play, or purge

### Example
>
> "All players simultaneously reveal 1 card from their hand."
> Revealed cards remain in hand after resolution.

---

## Hero states

**Exhausted** — hero state when unable to draw or play.
Hero skips their turn until the next wave.

---

## Tower states

**Silenced** — a tower that cannot trigger its effects this turn.
Silenced towers remain on the board and resume functioning
when the silence expires or is lifted.
Silence duration is defined by the effect that caused it.

**Banished** — a tower permanently removed from the board for the remainder of the scenario.
Banished towers do not return to any deck — they are out of the game until the next scenario.
Banishing is triggered voluntarily during the end-of-turn placement phase to free footprint
for a new tower. Multiple towers may be Banished simultaneously to accommodate a higher
footprint cost. The freed footprint is immediately available.

---

## Totem states

**Silence (totem)** — a totem that cannot trigger its effects for N turns.
The totem remains in the zone and counts toward capacity.
Effects resume automatically when Silence expires unless reapplied.

**Bury** — permanently reduce totem capacity by 1 for the remainder of
the scenario. The group chooses which totem is removed unless the effect
specifies otherwise. Buried totems cannot be recovered. The zone shrinks —
no empty slot remains.

---

## Enemy statuses

**Frozen** — enemy speed is reduced to 0 for 1 turn. The enemy does not move.
Transitions to Thawed at the end of that turn.
Triggered by any effect that applies Freeze.
If Burning is applied while Frozen: Shatter — remove Frozen, deal 2× Zeal damage.

**Thawed** — vulnerability state following Frozen. Lasts 1 turn.
Action cards may declare `if thawed` effects that trigger bonus output against this enemy.

**Emboldened** — enemy status triggered when Zeal ≤ 25% of max,
or when an adjacent enemy is Repelled this turn.
A cornered corporation fights harder.

**Thriving** — enemy buff status. A corporation doing well —
regenerates Zeal and gains momentum. Double meaning intentional.

**Corrupted** — enemy empowered by industrial pollution.
Gains Thriving stacks from poison instead of losing Zeal.
Direct counter to poison-specialist heroes.

**Erode N** — place N desolation tokens on the quadrant the enemy
currently occupies. If desolation tokens on that quadrant reach
its resilience value, the quadrant is Ravaged.

**Ravage N** — reduce global resilience by N permanently.
All quadrants become N points closer to being Ravaged.
Cannot be recovered within a scenario.

---

## Map status

**Occupied** — a tile that already contains one or more enemy meeples.

**Target tile** — the tile on which an effect is applied. The origin tile of the affected enemy or object at the moment the effect resolves.

**Destination tile** — the tile an enemy or object ends up on after a movement effect resolves.
Example: Push 1 moves an enemy from tile A1 (target) to tile A2 (destination).

**Ravaged** (quadrant state) — a quadrant whose desolation tokens
have reached its resilience threshold. All towers on a Ravaged
quadrant are permanently Silenced for the remainder of the scenario.

**Resilience** — the number of desolation tokens a quadrant can
absorb before becoming Ravaged. Defined on the scenario card.
Reduced globally by Ravage effects.

---

## Skill cooldowns

```yaml
cooldown:
  once_per_turn:  # tactical, frequent
  once_per_wave:  # strategic, meaningful
  once_per_game:  # ultimate, dramatic
```

---

## Card effect shorthand

```yaml
file: effects-vocabulary
```

## Combo multiplier

**🌀** — combo multiplier. Appended to an effect value, indicates
the effect scales with the current combo value.
Example: "Sap 3🌀" means "Sap (3 × combo)".
