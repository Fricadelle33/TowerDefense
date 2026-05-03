# Glossary

## Core vocabulary

**Sap** — reduce an enemy's Zeal. The primary output of hero actions.
Heroes sap enemy Zeal through card effects, tower effects, and status effects.

**Zeal** — an enemy's drive and organizational momentum. Replaces HP on all
enemy cards. When Zeal reaches 0, the enemy is Repelled.

**Repel** — the moment an enemy's Zeal reaches 0. The enemy meeple is removed
from the path. Triggers repel rewards immediately.

**Repel reward** — rewards granted instantly when an enemy is Repelled:
- XP awarded to the player who dealt the decisive sap
- Well cards dropped by elites, immediately available to add to any hero's deck
- Buy energy rewards stated on the enemy card

**Erode** — reduce land integrity. Triggered by enemies reaching objectives
or completing attacks against the Wights.

**Land integrity** — the Wights' shared HP pool, tracked on the board.
When land integrity reaches 0, the land is ravaged and players lose.

---

## Card actions

**Discard** — send a card from hand to the discard pile, triggering
`on_discard` effects. Grants 1 play energy.

**Dismiss** — forfeit your entire hand simultaneously. No individual card
resolution. No on_discard effects trigger. Grants +3 buy energy. Refreshes market.
Not a discard.

**Purge** — automatic end-of-turn hand clear. Silent — no effects trigger.
Cards go to discard pile.

**Reveal** — show a card from hand to all players without playing or
discarding it. The card remains in hand. Revealed cards may trigger
specific effects but are otherwise unaffected.

### Usage of Reveal
- Used by active skills and specific card effects
- All players may reveal simultaneously when an effect requires it
- Revealing does not count as a discard, play, or purge

### Example
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

---

## Enemy statuses

**Emboldened** — enemy status triggered when Zeal ≤ 25% of max,
or when an adjacent enemy is Repelled this turn.
A cornered corporation fights harder.

**Thriving** — enemy buff status. A corporation doing well —
regenerates Zeal and gains momentum. Double meaning intentional.

**Corrupted** — enemy empowered by industrial pollution.
Gains Thriving stacks from poison instead of losing Zeal.
Direct counter to poison-specialist heroes.

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

Card effects use terse verb + number notation:

| Notation      | Meaning                                                 |
|:--------------|:-----------------------------------------------------   |
| Sap N         | Reduce target enemy Zeal by N                           |
| Erode N       | Reduce land integrity by N                              |
| Poison N      | Apply N poison stacks to target                         |
| Push N        | Move target N tiles back along the path                 |
| Restore N     | Restore N land integrity                                |
| Reinforce N   | Add N durability to target tower                        |
| N🪙           | Generate N buy energy                                   |
| Silence N     | Silence target tower for N turns                        |
| Summon N      | Reveal the next N cards in the wave deck immediately    |
| Embolden N | Gain N Zeal at end of turn if no Sap was applied this turn |

Effects scale with combo formula unless stated otherwise.