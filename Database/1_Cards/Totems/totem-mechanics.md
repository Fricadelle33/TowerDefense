# Totems

## Role
Totems are shared, permanent engine pieces placed in the central totem zone.
They do not multiply passively — they **react** to play patterns, board states,
and combo values. Totems are targets to build toward, not bonuses that apply
automatically.

> To discard is to sow, to play is to reap. Totems are the harvest condition.

---

## Rules

### Placement
- Starting capacity: 5 totem slots in the shared zone
- Never in any player's deck
- All players benefit from all active totems
- Awarded by: 
  - Low-tier: Contract completion, elite repels, level-up unlocks
  - High-tier: Fairy Well 
- If at capacity: group negotiates which totem to replace. Replaced totems are removed from the game. 

### Silence
Elites may Silence one or more totems as an ability.
- A Silenced totem cannot trigger its effects for N turns
- The totem remains in the zone and counts toward capacity
- Effects resume automatically when Silence expires
- Silence can be reapplied before it expires

### Bury
Only bosses can Bury totems.
- Permanently reduces totem capacity by 1 for the remainder of the scenario
- The group chooses which totem is Buried, unless the boss card specifies otherwise
- Capacity can never be restored within a scenario
- A buried totem is gone — no empty slot remains, the zone simply shrinks

```
Starting:     [ T ][ T ][ T ][ T ][ T ]   capacity: 5
After 1 Bury: [ T ][ T ][ T ][ T ]        capacity: 4
After 2 Bury: [ T ][ T ][ T ]             capacity: 3
```

> A boss that can Bury twice is a scenario-defining encounter.
> Players will remember the run where they lost 2 totem slots and still won.

---

## Totem types

| Type | Trigger | Feel |
|:---|:---|:---|
| **Threshold** | Combo reaches N | Rewards deep combos — push further for more |
| **Conditional** | Board state condition met | Rewards reading the board and playing around it |
| **Conversion** | Output type redirected | Transforms what a hero does, not just how much |
| **Resonance** | Another player's action this turn | Cooperative engine — two heroes synergizing |
| **Resource** | Permanent, always active | Changes the economics of play — build faster, build more |

---

## Template

```yaml
name: Venom Idol
type: totem
element: water
effect_type: poison
totem_type: threshold       # threshold | conditional | conversion | resonance | resource
trigger: combo ≥ 4          # omit for resource totems — always active
effect: >
  Also apply Poison equal to (combo − 3) to target enemy.
awarded_by:
  - contract: TBD
  - elite: TBD
  - level: TBD
tags: [water, poison, threshold]
```

---

## Design notes

### Option C — Balatro-style layering (locked)
Totems do not modify cards. They **watch what happens and react**.
Base card output is untouched. The totem triggers on combo value
and adds a secondary output on top.

```
Combo 3: Sap 3 only
Combo 4: Sap 4 + Poison 1     ← totem triggers
Combo 5: Sap 5 + Poison 2
Combo 6: Sap 6 + Poison 3
```

### Silence — Elites
Elites may carry a `silence_totem` ability on their card.

```yaml
# Example elite ability
on_reach_tile:
  silence_totem: 2      # silences a totem of the group's choice for 2 turns
```

### Bury — Bosses only
Only bosses can permanently reduce totem capacity.

```yaml
# Example boss ability
on_trigger:
  bury: totem:any       # group chooses which totem is buried
  bury: totem:water     # boss targets a specific element's totem
```

> Bury is a non-eliminatory defeat condition.
> The game continues — but the engine is permanently scarred.

---

## Glossary additions

**Silence (totem)** — a totem that cannot trigger its effects for N turns.
The totem remains in the zone and counts toward capacity.
Effects resume automatically when Silence expires unless reapplied.

**Bury** — permanently reduce totem capacity by 1 for the remainder of
the scenario. The group chooses which totem is removed unless the effect
specifies otherwise. Buried totems cannot be recovered. The zone shrinks —
no empty slot remains.