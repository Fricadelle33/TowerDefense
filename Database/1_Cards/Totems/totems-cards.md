# Totem cards

## Totem card template

```yaml
name: slug
type: totem
element: water          # or any
effect_type: poison     # sap | poison | heal | push | reinforce | footprint | economy
totem_type: threshold   # threshold | conditional | conversion | resonance | resource
trigger: combo ≥ 4      # omit for resource totems
effect: >
  Effect description.
awarded_by:
  - contract: TBD
  - elite: TBD
  - level: TBD
tags: [water, poison, threshold]
loop-risk: false
```

## Threshold totems

```yaml
name: Venom Idol
totem_type: threshold
element: water
effect_type: poison
trigger: combo ≥ 4
effect: >
  Also apply Poison equal to (combo − 3) to target enemy.
note: >
  Croc's Sap output is untouched. The totem converts excess combo
  into poison. Incentivizes pushing combos past the Repel threshold.
tags: [water, poison, threshold]
```

```yaml
name: Pruning Idol
totem_type: threshold
element: any
effect_type: remove
trigger: combo ≥ 5
effect: >
  Remove 1 card from your hand or discard pile.
note: >
  Turns deep combos into deck-thinning events.
  The trim engine — rewards building long chains beyond damage needs.
tags: [any, remove, threshold]
```

```yaml
name: Tide Surge
totem_type: threshold
element: water
effect_type: sap
trigger: combo ≥ 4
effect: >
  Double all water output this turn.
note: >
  High ceiling, hard to reach. Deck-thinning matters —
  you need a lean deck to hit 4+ consistently.
tags: [water, sap, threshold]
```

```yaml
name: Resonant Spire
totem_type: resource
element: any
effect_type: tower
effect: All towers may fire twice per enemy turn.
note: >
  Doubles tower output globally. Extremely powerful —
  award only in late scenarios or as a tier-3 contract reward.
tags: [any, tower, resource]
```

---

## Conditional totems

```yaml
name: Sanctuary Idol
totem_type: conditional
element: any
effect_type: heal
trigger: no enemies on the path at end of player turn
effect: >
  Restore land integrity equal to your combo value.
note: >
  Rewards clearing waves completely.
  Creates a defensive engine — heroes coordinate to clear the board,
  not just Repel the most dangerous enemy.
tags: [any, restore, conditional]
```

```yaml
name: Prism Idol
totem_type: conditional
element: any
effect_type: sap
trigger: discard 1 card of each element this turn
effect: >
  Multiply combo output ×3 this turn.
note: >
  Rewards mixed-hand management over mono-element purity.
  Punishes greedy mono-element decks — forces situational flexibility.
  Extremely powerful, requires preparation.
loop-risk: true             # flag for playtesting — may trivialize late waves
tags: [any, multiplier, conditional]
```

---

## Conversion totems

```yaml
name: Venom Tide
totem_type: conversion
element: water
effect_type: poison
trigger: on play
effect: >
  Your Sap output converts to Poison stacks at 1:1.
  Poison stacks applied this turn also Sap 1.
note: >
  Croc becomes a full poison hero — Sap and Poison merge.
  Changes hero identity, not just output magnitude.
tags: [water, poison, conversion]
```

```yaml
name: Deep Current
totem_type: conversion
element: water
effect_type: sap
trigger: your first 3 cards played this turn are all water
effect: >
  Your next water card this turn counts as 2 for combo calculation.
note: >
  Cascade engine — rewards committing fully to water early in the turn.
  No cross-turn tracking required.
tags: [water, sap, conversion]
```

---

## Resonance totems

```yaml
name: Storm Pact
totem_type: resonance
element: water
effect_type: sap
trigger: another player played air cards this turn
effect: >
  Your water combo gains +2 to card count this turn.
note: >
  Cooperative engine — water and air heroes synergize through the totem.
  Encourages element specialization and cross-player coordination.
tags: [water, air, resonance]
```

## Resource totems

Resource totems are always active — no trigger condition.
They permanently modify the economics of play for the entire group.

```yaml
name: Tidal Foundation
totem_type: resource
element: water
effect_type: footprint
effect: All water towers cost 2 less footprint.
note: >
  Enables water-specialist heroes to flood the board with towers
  without competing for footprint with teammates.
  Synergizes directly with water-element heroes and tower-heavy builds.
tags: [water, footprint, resource]
```

```yaml
name: Deep Roots
totem_type: resource
element: any
effect_type: footprint
effect: The shared footprint pool increases by 3.
note: >
  Pure economic expansion — lets the group run more towers simultaneously.
  No element restriction. Universally useful, never wasted.
tags: [any, footprint, resource]
```

```yaml
name: Trade Winds
totem_type: resource
element: air
effect_type: economy
effect: All tier-1 market cards cost 1🪙 less.
note: >
  Accelerates early-game deck building.
  Pairs well with market-runner archetypes.
tags: [air, economy, resource]
```

```yaml
name: Ancient Cache
totem_type: resource
element: any
effect_type: economy
effect: Accessing The Burrow costs 2🪙 instead of 4🪙.
note: >
  Unlocks hero development at half price.
  Rewards heroes who invest in their Burrow deck.
tags: [any, burrow, resource]
```

```yaml
name: Fertile Ground
totem_type: resource
element: ground
effect_type: economy
effect: Dismiss grants +5🪙 instead of +3🪙.
note: >
  Makes Dismiss a viable economic strategy rather than a desperate move.
  Pairs well with market-runner and discard-engine archetypes.
tags: [ground, economy, resource]
```
