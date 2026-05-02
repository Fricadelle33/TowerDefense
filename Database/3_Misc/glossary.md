## Dismiss

**Dismiss** — forfeit your entire hand with no individual card resolution.
Not a discard. on_discard effects do not trigger.

## Reveal

**Reveal** — show a card from your hand to all players without
playing or discarding it. The card remains in hand.
Revealed cards may trigger specific effects but are otherwise unaffected.

### Usage
- Used by active skills and specific card effects
- All players may reveal simultaneously when an effect requires it
- Revealing does not count as a discard, play, or purge

### Example
> "All players simultaneously reveal 1 card from their hand."
> Revealed cards remain in hand after resolution.

## Cooldown 
~~~yaml
cooldown:
  once_per_turn:  # tactical, frequent
  once_per_wave:  # strategic, meaningful
  once_per_game:  # ultimate, dramatic
~~~

---


**Discard** — send a card from hand to discard pile, triggering 
`on_discard` effects. Grants 1 play energy.

**Dismiss** — forfeit entire hand simultaneously. No effects trigger.
Grants +3 buy energy. Refreshes market.

**Purge** — automatic end-of-turn hand clear. Silent, no effects trigger.

**Reveal** — show a card from hand to all players without playing 
or discarding it. Card remains in hand.

**Exhausted** — hero state when unable to draw or play. 
Hero skips turn until next wave.

**Thriving** — enemy buff status. Fits the lore double meaning:
a corporation doing well.

**Corrupted** — enemy empowered by industrial pollution. 
Gains strength from poison instead of being weakened by it.