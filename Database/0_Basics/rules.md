# Rules

## Lore
The Wights are ancient spirits embodying the living land.
They cannot fight — they can only endure. Animal heroes are
their last line of defense against waves of industrial destruction.

---

## Players
2 to 4 players. Each player controls one hero for the duration of the scenario.

---

## Win condition
Survive all waves in the scenario without meeting a lose condition.
If the scenario has a boss, the boss must be Repelled to win.

---

## Lose conditions
Meeting any lose condition ends the game immediately.

1. **The land is ravaged** — land integrity reaches 0
2. **Objectives failed** — enemies complete all
   scenario-specific objectives (defined on the scenario card)
3. **All heroes are exhausted** — no hero can draw or
   play cards this wave

> Lose conditions 1 and 2 are always active.
> Lose condition 3 is a wave-level condition —
> heroes recover at the start of the next wave.

---

## The Wights

In standard scenarios, the Wights are represented as a shared
land integrity pool tracked on the board. Heroes defend them collectively.

In VIP scenarios, one or more Wights are represented as meeples
on the path with individual land integrity and movement. Enemies may
prioritize targeting them. Specific rules are defined on the scenario card.

---

## Hero exhaustion
A hero is exhausted when they cannot draw cards AND have no
cards in hand or deck. Exhausted heroes:
- Skip their player turn
- May still benefit from shared totem effects
- Recover fully at the start of the next wave

---

## Play sequence

Each wave consists of repeated rounds until the wave is cleared
or a lose condition is met.

### Turn order

All players can play in the order they choose, 
but players must complete their turns before switching to the next.

### 1. Player turn
Resolve sequentially, starting from the first player then clockwise:

**a. Play phase**
- Discard cards to generate play energy (1 discard → 1 play)
- Play cards from hand using play energy or free_plays counter
- Buy cards from market using buy energy
- Resolve all effects, Zeal-sap, and status triggers

**b. Dismiss** *(optional)*
- Forfeit remaining hand
- Gain +3 buy energy immediately
- Market refreshes

**c. End of player turn**
- Purge remaining hand (silent — no effects trigger)
- Draw up to `hero:starting_hand_size`

### 2. Enemy turn
Resolve per enemy, sequentially from furthest along path to closest:

1. **Per-turn effects** — Erode N, Ravage N, Summon N, Embolden check
2. **Status ticks**
   - Poison: lose Zeal equal to stack count, stack count decreases by 1
   - Burning: lose 1 Zeal, check propagation
3. **Move** — advance speed tiles along path

After all enemies have moved:

4. **Tower effects** — for each tower on the board:
   - If no enemy is within attack pattern range: tower does not fire
   - `targets: single` → fire at highest priority enemy in range
   - `targets: AoE` → fire at all enemies in range simultaneously
   - Apply terrain_affinity modifiers
5. **Objective reached** — for each enemy now at the exit:
   - Trigger on_reach_exit effect
   - Erode current quadrant
   - Remove meeple — no repel rewards

### 3. End of round
- Decrement all status durations (burning, frozen, thawed)
- Resolve `emboldened` triggers (zeal ≤ 25% check)
- Check lose conditions
- Begin next round or, if wave deck is depleted, advance to end-of-wave phase

---

## Waves

### What is a wave
A wave is a defined set of enemy cards drawn and revealed one per
player turn. Each scenario defines its waves explicitly.

```yaml
# Example wave definition
wave-1:
  standard: 3
  elite: 0
  bonus: null

wave-2:
  standard: 4
  elite: 1
  bonus: "If fast-forwarded: each hero draws 2 cards"
```

Wave cards are shuffled face-down into a wave deck at wave start.
Each player turn, one enemy card is revealed and its meeple
placed at the path entry point.

Exception: summoner enemies may reveal additional cards
immediately upon entering the path. Summoned enemies are placed
at the summoner's current position and do not count toward
wave deck exhaustion.

---

### Wave exhaustion

When the wave deck is exhausted, players choose one of:

#### Fast-forward
- Immediately trigger end-of-wave phase
- Claim the bonus printed on the wave card
- No respite turns granted

#### Respite
- Attempt to gain N turns before the next wave
- **Respite test**: all players simultaneously reveal 1 card
  from hand. If (player_count − 1) or more cards share the same element,
  gain N respite turns.
- `respite_turns = floor(wave_card_count / player_count)`
  minimum: 1 if respite test passed. If respite_turns < 1, respite is impossible.
- During respite turns: no new enemies enter the path,
  existing enemies still advance and act
- After respite turns: end-of-wave phase triggers

---

### End-of-wave phase

Triggers after fast-forward or after respite turns expire.

1. **Reveal** next wave card — read wave composition and bonus
2. **Build** next wave deck — shuffle standard and elite cards face-down
3. **Prepare** meeples — assign one meeple per enemy card
4. **Begin** next wave

---

## End-of-scenario phase

1. **Collect** the boss reward (if any)
2. **Resolve** contract completions
3. **Gain** scenario rewards based on completion threshold
4. **Reset** hero XP and levels. **Discard** all totems, played cards, remaining enemies and put them back in their respective decks.
5. **Discard** the path

> XP and levels are scenario-scoped. Campaign progression is expressed through
> permanent deck improvements: Fairy Well cards, scenario rewards, and
> Burrow cards acquired during the run. Each scenario starts all heroes at level 1.

If you'd like to pursue, replay game-setup

---

## Card types

### Player cards
- **Action** — one-use card played from hand, discarded after resolution
- **Tower** — placed on the board, persists between turns,
  affects enemies on or adjacent to its hex tile
- **Totem** — placed in the shared totem zone, never in any deck,
  provides permanent combo multipliers

### Enemy cards
- **Standard** — wave filler, defined speed / Zeal / effect
- **Elite** — named enemy, unique abilities, can drops Well rewards on Repel
- **Boss** — scenario-specific Elite, win condition tied to Repelling (TBD)

---

## Repel rewards
When an enemy's Zeal reaches 0 and they are Repelled,
rewards trigger immediately:
- XP awarded to the player who dealt the decisive sap
- Well cards dropped by elites are immediately available
  to add to any hero's deck
- Buy energy rewards (if stated on enemy card) granted
  to the player who dealt the decisive sap