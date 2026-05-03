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

**Land integrity** — the Wights' shared integrity pool, tracked on the board.
When land integrity reaches 0, the land is ravaged and players lose.

**Slow N** — reduce enemy speed by N this turn.
If speed reaches 0 or below, the enemy does not move.
Frozen is Slow equal to the enemy's full speed stat.


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

**Remove** — permanently remove a card from your hand or discard pile.
Removed cards leave the game for this scenario.
Removed cards are not discarded — no on_discard effects trigger.

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

## Totem states

**Bury** — permanently remove 1 totem from the shared zone.
The maximum totem capacity decreases by 1 for the remainder
of the scenario. Buried totems cannot be recovered.
The player group chooses which totem is buried unless
the effect specifies otherwise.

**Silence (totem)** — a totem that cannot trigger its effects
for N turns. The totem remains in the zone. Effects resume
automatically when silence expires unless reapplied.

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

**Erode N** — place N desolation tokens on the quadrant the enemy
currently occupies. If desolation tokens on that quadrant reach
its resilience value, the quadrant is Ravaged.

**Ravage N** — reduce global resilience by N permanently.
All quadrants become N points closer to being Ravaged.
Cannot be recovered within a scenario.

---

## Map status

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

Card effects use terse verb + number notation:

| Notation      | Meaning                                                     |
|:--------------|:-----------------------------------------------------       |
| Sap N         | Reduce target enemy Zeal by N                               |
| Ravage N      | Reduce global resilience by N permanently.                  |
| Erode N       | Reduce land integrity by N                                  |
| Poison N      | Apply N poison stacks to target                             |
| Push N        | Move target N tiles back along the path                     |
| Restore N     | Restore N land integrity                                    |
| N🪙           | Generate N buy energy                                       |
| Silence N     | Silence target tower for N turns                            |
| Summon N      | Reveal the next N cards in the wave deck immediately        |
| Embolden N    | Gain N Zeal at end of turn if no Sap was applied this turn  |


Effects scale with combo formula unless stated otherwise.