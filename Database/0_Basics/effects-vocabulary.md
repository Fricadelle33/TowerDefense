# Effects Syntax

> Canonical grammar for card effects. Use strict vocabulary.

## Combo Notation (🌀)

- Meaning: Value × current combo (e.g., `Sap 3🌀`).
- Valid modifiers: Sap, Poison, Push, Burn, Slow, Reveal, Restore, Barrier.
- INVALID modifiers: 🪙, Draw, Remove, XP, Silence, Embolden, Bury, Summon, Ravage.

## Core Verbs (Player & Tower)

- `Sap N`: Reduce target enemy Zeal by N.
- `Poison N`: Apply N poison stacks (decrements by 1 each turn).
- `Push N`: Move target enemy N tiles backward (Sap remaining if past entry).
- `Restore N`: Restore N land integrity on most-eroded active quadrant.
- `Silence N`: Target tower/totem cannot trigger effects for N turns.
- `Slow N`: Reduce target enemy speed by N for 1 turn (Speed 0 = Frozen).
- `Burn`: Apply burning (lose 1 Zeal/turn for 1 turn). Refreshes duration.
- `Remove N`: Permanently remove N cards from hand/discard for scenario.
- `Upgrade (card)`: Remove card from deck, replace with drawn card.
- `Reveal N`: Show N cards from hand to all players, return to hand.
- `Repel`: Immediately remove enemy from board. Trigger rewards.
- `Draw N`: Draw N cards.
- `N🪙`: Generate N buy energy. Resets at end of turn.
- `XP N`: Grant N XP.
- `Purge N (card)`: Put card from hand to discard. No `on_discard` trigger.
- `Remove N (card)`: Permanently remove card from hand/discard.
- `Remove E (effect)`: Cure all specified effects from target.
- `Barrier N`: Place N barrier tokens on quadrant. 1 block = 1 desolation.
- `Tick (Poison)`: Trigger poison stack effect (Sap 1) before end-of-turn.
- `Trigger`: Force conditional effect.
- `Seal (effect)`: Enemy cannot gain or lose this effect this turn. Existing effects still apply.
- `Lend (card)`:  Place this card on a player's play area. It counts towards their combo. Return this card end of turn.

## Enemy Verbs

- `Erode N`: Place N desolation tokens on current quadrant.
- `Ravage N`: Permanently reduce global resilience by N.
- `Summon N`: Reveal next N wave cards, place at path start.
- `Embolden N`: If no Sap applied this turn, gain N Zeal at end of turn.
- `Bury (totem)`: Permanently reduce totem capacity by 1.
- `Purge N (card)`: Players collectively remove N cards from hands.
- `Immune to S (status)`: Cannot be affected by status S.

## Conditional Syntax

- `If combo ≥ N → [effect]`
- `If element is [element] → [effect]`
- `If target is [status] → [effect]`
- `If [board_state] → [effect]`
- `If [player_state] → [effect]`
- `[Condition] → [effect] instead` (Replaces base effect entirely).
- `[Condition] → also [effect]` (Adds to base effect).
- `[Condition] → 🌀±X` (Adds X to combo).
- `[Condition] → ±X[resource]` (Adds X resource).

## Resolution Order

1. Base effect.
2. `status_triggers` check (Replaces Step 1 if "instead").
3. `terrain_affinity` check.
4. Combo bonuses (totems).
5. `on-play` effects (totems).

## Metadata Standards

- `slug`: `card:[lowercase-hyphenated-name]`
- `element: [type1, type2]` (Dual-element requires player declaration on play).
- Mandatory declarations: `loop-risk` (if true), `requires_facing` (towers), `tier` (except starters and burrows), `cost` (except starters).