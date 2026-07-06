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
TOWERDEFENSE
|   .claudesignore
|   .gitignore
|   LICENSE
|   README.md
|   
+---.claude
|   |   claude-context.md
|   |   
|   \---agents
|           agents.xml
|           
+---Database
|   +---0_Basics
|   |       0-getting-started.md
|   |       design-guidelines.md
|   |       economy-and-engine.md
|   |       effects-vocabulary.md
|   |       effects.md
|   |       game-setup.md
|   |       lore.md
|   |       market.md
|   |       rules.md
|   |       
|   +---1_Cards
|   |   +---Actions
|   |   |       action-t1-cards.md
|   |   |       action-t2-cards.md
|   |   |       action-template.md
|   |   |       
|   |   +---Enemies
|   |   |       enemies-elite.md
|   |   |       enemies-movement.md
|   |   |       enemies-standard.md
|   |   |       
|   |   +---Fairy Well
|   |   |       fairy-well-cards.md
|   |   |       fairy-well.md
|   |   |       
|   |   +---Heroes
|   |   |   |   hero-mechanics.md
|   |   |   |   
|   |   |   \---0_Croc
|   |   |           hero-croc-burrow.md
|   |   |           hero-croc-cards.md
|   |   |           hero-croc.md
|   |   |           
|   |   +---Totems
|   |   |       totem-cards.md
|   |   |       totem-mechanics.md
|   |   |       totem-template.md
|   |   |       
|   |   \---Towers
|   |           tower-attack-patterns.svg
|   |           tower-attacks.md
|   |           tower-cards.md
|   |           tower-placement.md
|   |           tower-template.md
|   |           
|   +---2_Board
|   |   |   contracts.md
|   |   |   printing_constraints.md
|   |   |   scenarios.md
|   |   |   
|   |   \---Material
|   |           hex-tiles.md
|   |           mat.md
|   |           material-list.md
|   |           
|   \---3_Misc
|           glossary.md
|           trad-fr.md
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
| Enemy (individuals) | Gloomer |
| Enemy (entity) | The Tide |
| Kill/defeat | Repel |
| Deal damage | Sap |
| Damage to land | Erode (quadrant) / Ravage (global) |
| Enraged | Emboldened |
| Blessed | Thriving |
| Armor (enemy) | Shield |

## Card effect shorthand

```yaml
file: [effects, effects-vocabulary]
```

## Key mechanics 

### Summary

```yaml
file: [rules, economy-and-engine]
```

### Towers

```yaml
file: [tower-attacks, tower-placement]

```

### Totems

```yaml
file: totem-mechanics
```

### Hero mechanics, progression and XP 

```yaml
file: hero-mechanics
```

### The Fairy Well

```yaml
file: fairy-well
```

### Markets

```yaml
file: market
```

---

## Card templates

### Action cards

```yaml:
file: action-template
```

### Tower card

```yaml
file: tower-template
```

### Enemy card (standard/elite)

```yaml
file: enemies-template
```

### Hero card

```yaml
file: hero-mechanics
```

### Totem card

```yaml
file: totem-template
```

### Contract card

```yaml
file: contract-template
```

### Scenario card

```yaml
file: scenario-tempalte
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
