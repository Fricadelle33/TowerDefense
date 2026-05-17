# Design Guidelines

> Balance ranges, archetypes, and anti-patterns for engine tuning.

## Tier Balance Ranges

| Effect | Tier 1 (1-3🪙) | Tier 2 (3-5🪙) | Tier 3 (5-8🪙) |
|---|---|---|---|
| Sap | 1-3 | 3-5 | 5-8+ (scaling) |
| Poison | 1 | 2-3 | 3+ (scaling) |
| Push | 1 | 1-2 | 2-3 |
| Restore | 1 | 2 | 3+ |
| Slow | 1 | 1-2 | 2+ |
| Draw | N/A | 1 (cond.) | 1-2 (cond.) |
| Remove | N/A | 1 (cond.) | 1-2 |
| 🪙 Gen | 1-2 | 2-4 | 4-6 |
| Cond. Bonus | +1 to +2 | +2 to +4 | +3 to +6 |

> **Flag**: Tier 2+ cards combining `Draw` + `🪙` on `on_discard` must have `loop-risk: true`.

## Element Archetypes

- **Water** (Flowing, persistent): Sap, Poison, Push. *Avoid*: Burn, Reinforce.
- **Leaves** (Growth, regeneration): Restore, Poison, propagation. *Avoid*: Push, raw Sap.
- **Ground** (Solid, breaking): Reinforce, shield-pierce, AoE. *Avoid*: Subtle status, fast triggers.
- **Air** (Movement, reveal): Slow, Reveal, Push, Draw. *Avoid*: Raw damage, persistent status.

## Coop Patterns (Required)

- **Setup**: Apply status without payload.
- **Payoff**: Use `status_triggers` to reward setup.
- **Combo Extender**: Help others hit thresholds (e.g., reveal/draw based on ally element).
- **Resource Sharer**: Transfer 🪙/XP to ally.

## Forbidden Patterns (Anti-Patterns)

- **Lock-and-key**: Hard counters with no general alternative.
- **Archetype wipe**: Nullifying a build type without recourse.
- **Forced losses**: Wave auto-fails with no player agency.
- **Mass untargeted status**: Board-wide debuffs lacking scaling logic.
- **Discard punishment**: Effects that penalize engine cycling.
- **Permanent hero elimination**: Exhaustion is fine; removal is banned.

## Naming & Lore

- 2-4 words, evocative.
- Zero generic verbs (e.g., ban "Strike", "Attack").
- Concrete imagery (e.g., "Croc Roll", "Swamp Gas").
- Serious tone without taking itself too seriously.
