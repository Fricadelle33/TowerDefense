# Tower Defense — Claude Code Context

## Read order

1. `.claude/claude-context.md` (this file / already read)
2. `.claude/agents/[relevant].md`
3. `Database/` files relevant to the task

## Project overview

This is a board game database for an asymmetrical cooperative tower defense game
with deck-building mechanics, character leveling, and combo-driven engine building.
The database is written in Markdown with YAML card/entity definitions.
The project is pre-print — this is a digital proof of concept intended for
eventual physical printing.

## Repository

<https://github.com/Fricadelle33/TowerDefense>

## Project structure

```text
.claude/
  claude-context.md       # this file
  agents/
    strict_validator.md
    market_supervisor.md
    creative_player.md
    adversarial_gm.md
    rotating_player.md

Database/
  _Internal/
    __toDo                # authoritative open-issues list
  0_Basics/
    0-getting-started.md
    rules.md
    economy-and-engine.md
    game-setup.md
    lore.md
  1_Cards/
    effects.md            # status effect definitions
    effects-vocabulary.md # canonical card-writing language reference
    market.md             # market mechanics (shared market)
    fairy-well.md         # The Fairy Well deck mechanics
    Action/
      t1-action-cards.md
      t2-action-cards.md
    Enemies/
      enemies-standard.md
      enemies-elite.md
      enemies-movement.md
    Heroes/
      hero-mechanics.md
      0_Croc/
        hero-croc.md
        hero-croc-cards.md
        hero-croc-burrow.md
    Towers/
      towers.md
      tower-placement.md
      tower-attacks.md
      tower-attack-patterns.svg
    Totems/
      totems-mechanics.md
      totems-cards.md
  2_Board/
    contracts.md
    scenarios.md
    Material/
      mat.md
      hex-tiles.md
      material-list.md
  3_Misc/
    glossary.md
    trad-fr.md
```

## Design philosophy

- Tone: serious without taking itself seriously
- Core loop: asymmetrical cooperative tower defense + deck building
- Combo engine: Balatro-style reactive totems, element-based combos
- Vocabulary: no combat language — Sap/Repel/Erode/Ravage not kill/damage/HP

---

## Core vocabulary (CRITICAL — never use old terms)

| Old term | New term |
| --- | --- |
| HP (enemy) | Zeal |
| HP (Wights/land) | land integrity |
| Kill/defeat | Repel |
| Deal damage | Sap |
| Damage to land | Erode (quadrant) / Ravage (global) |
| Enraged | Emboldened |
| Blessed | Thriving |
| Armor (enemy) | Shield |

## Card effect shorthand

```yaml
file: [Database/1_Cards/effects, Database/1_Cards/effects-vocabulary]
```

## Key mechanics 

### Summary

```yaml
file: [Database/0_Basics/rules, Database/0_Basics/economy-and-engine]
```

### Towers

```yaml
file: [Database/1_Cards/Towers/tower-attacks,
       Database/1_Cards/Towers/tower-placement]

```

### Totems

```yaml
file: Database/1_Cards/Totems/totem-mechanics
```

### Hero mechanics, progression and XP 

```yaml
file: Database/1_Cards/Heroes/hero-mechanics
```

### The Fairy Well

```yaml
file: Database/1_Cards/Fairy Well/fairy-well
```

### Markets

```yaml
file: Database/1_Cards/Market/market.md
```

---

## Card templates

### Action cards

```yaml:
file: Database/1_Cards/Market/market
```

### Tower card

```yaml
file: Database/1_Cards/Towers/tower-cards
```

### Enemy card (standard/elite)

```yaml
file: [Database/1_Cards/Enemies/enemies-standard,
       Database/1_Cards/Enemies/enemies-elite]
```

### Hero card

```yaml
file: Database/1_Cards/Heroes/hero-mechanics
```

### Totem card

```yaml
file: Database/1_Cards/Totems/totems-cards
```

### Contract card

```yaml
file: Database/2_Board/contracts
```

### Scenario card

```yaml
file: Database/2_Board/scenarios
```

---

## Agents

Five specialized agents live in `.claude/agents/`. Each runs in an isolated
context window. Invoke explicitly or rely on automatic delegation when the
agent's `description` matches the task.

| Agent | Role |
|---|---|
| `strict_validator` | YAML compliance, required fields, value ranges, vocabulary, cross-references |
| `market_supervisor` | Genre failure modes for TD, deck-builder, roguelike-deckbuilder spaces |
| `adversarial_gm` | Plays enemies optimally to expose enemy design weaknesses |
| `creative_player` | Plays heroes as a min-maxer hunting OP combos and infinite loops |
| `rotating_player` | Cycles through 5 casual personas to test accessibility and retention |
