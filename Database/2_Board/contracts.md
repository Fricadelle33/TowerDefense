# Contracts

## Role
Contracts are optional side-challenges that run alongside the main scenario.
They are fun, specific, and personality-driven — closer to dares than objectives.
Completing contracts fuels the engine: new totems, Well cards, buy energy, and
more contracts.

> Contracts are not scenario objectives. They don't define how you win or lose.
> They define how boldly you play.

---

## Contract deck

Each scenario seeds a shuffled contract deck at setup.

```yaml
# In scenario template
contracts:
  wave_reward: 1        # contracts revealed per wave cleared
  deck_size: 12         # total contracts in the deck for this scenario
  chain: true           # completing a contract reveals 1 additional contract
```

- No contracts are visible at scenario start
- If the contract list is empty, each wave cleared reveals 1 contract from the deck
- Completing a contract immediately reveals 1 more
- The chain continues until the deck is exhausted
- The last contract will often be a high risk high reward
- Contracts are **opt-in** — the group decides whether to attempt each one

---

## Opt-in and failure

When a contract is revealed, the group may:
- **Accept** — commit to attempting the objectives. Curse activates on failure.
- **Decline** — ignore the contract. No reward, no curse, no chain reveal.

Accepting is always a risk/reward decision. Declining is always an opportunity cost.
In the rare event that a contract cannot be executed with the current hero composition, discard and draw a new one. 
---

## Contract tiers

| Tier | Scope | Typical reward |
|:---|:---|:---|
| 1 | Single turn or single wave | 🪙, Well card, minor totem |
| 2 | Multi-wave, requires planning | Powerful totem, Burrow access |
| 3 | Scenario-spanning, epic condition | Unique totem, permanent campaign bonus |

Early waves surface tier-1 contracts. As the deck depletes, tier-2 and tier-3
naturally emerge — escalating the side-quest pressure alongside wave difficulty.

---

## Contract categories

| Category | Feel | Example condition |
|:---|:---|:---|
| **Combo** | Reward engine play | Play a 5-card water combo in one turn |
| **Repel** | Reward specific repels | Repel an Emboldened enemy |
| **Survival** | Reward board control | End a wave with Q1 untouched |
| **Hero** | Reward hero-specific play | Trigger Deathmatch successfully |
| **Sacrifice** | High risk, high reward | Accept Ravage 1 now — survive the next wave |
| **Cooperative** | Reward cross-player coordination | All heroes play the same element in one round |

---

## Template

```yaml
name: contract-slug
flavor: >
  One evocative sentence. Personality over description.
category: combo           # combo | repel | survival | hero | sacrifice | cooperative
hero: null                # hero:slug if hero-specific, null if any hero
tier: 1                   # 1 | 2 | 3
difficulty: 2             # 1-5, back office reference

objectives:
  - id: obj-1
    description: Human-readable condition
    condition: machine-readable condition slug

rewards:
  - objectives_met: 1
    reward:               # 🪙, well card, totem, burrow access, etc.
chain: true               # always true — completing reveals 1 more contract

curse:
  trigger: accepted and obj-1 not met
  effect: mechanic effect
  flavor: >
    One evocative sentence. The land pays the price.
```

---

## Example contracts

### Tier 1

```yaml
name: contract:cold-blooded
flavor: >
  Croc doesn't sweat. He calculates.
category: combo
hero: hero:croc-o-dill
tier: 1
difficulty: 2

objectives:
  - id: obj-1
    description: Play a 5-card water combo in a single turn
    condition: combo:element:water >= 5

rewards:
  - objectives_met: 1
    reward: 3🪙 per hero
chain: true

curse:
  trigger: accepted and obj-1 not met
  effect: Erode 2 on Q1
  flavor: >
    The swamp grows cold and still.
```

---

```yaml
name: contract:no-mercy
flavor: >
  Don't let them breathe.
category: repel
hero: null
tier: 1
difficulty: 1

objectives:
  - id: obj-1
    description: Repel 2 enemies in the same player turn
    condition: repel:count >= 2 in single:player-turn

rewards:
  - objectives_met: 1
    reward: well-card:TBD
chain: true

curse:
  trigger: accepted and obj-1 not met by wave-end
  effect: Erode 1 on current quadrant
  flavor: >
    They regrouped. The land felt it.
```

---

```yaml
name: contract:pristine
flavor: >
  Not a single scar.
category: survival
hero: null
tier: 1
difficulty: 2

objectives:
  - id: obj-1
    description: End a wave with no desolation tokens on Q1
    condition: desolation:Q1 = 0 at wave-end

rewards:
  - objectives_met: 1
    reward: Restore 2 on Q1
chain: true

curse:
  trigger: accepted and obj-1 not met
  effect: Erode 3 on Q1
  flavor: >
    What you failed to protect, you now owe.
```

---

### Tier 2

```yaml
name: contract:four-winds
flavor: >
  The land speaks every language. Do you?
category: cooperative
hero: null
tier: 2
difficulty: 3

objectives:
  - id: obj-1
    description: All heroes play the same element in the same round
    condition: element:all-heroes-same in single:round
  - id: obj-2
    description: Do it twice in the same wave
    condition: element:all-heroes-same in single:round, count >= 2

rewards:
  - objectives_met: 1
    reward: 4🪙 per hero
  - objectives_met: 2
    reward: totem:storm-pact
chain: true

curse:
  trigger: accepted and obj-1 not met by wave-end
  effect: Silence 2 on a totem of the group's choice
  flavor: >
    Discord weakens the land's voice.
```

---

```yaml
name: contract:no-towers
flavor: >
  Claws and instinct. Nothing else.
category: repel
hero: null
tier: 2
difficulty: 4

objectives:
  - id: obj-1
    description: Repel an elite without any tower contributing Zeal-sap
    condition: elite:repelled and tower:zeal-sap-contributed = 0

rewards:
  - objectives_met: 1
    reward: well-card:TBD
chain: true

curse:
  trigger: accepted and obj-1 not met
  effect: Ravage 1
  flavor: >
    You relied on stone when you should have relied on each other.
```

---

```yaml
name: contract:unmatched-trigger
flavor: >
  One shot. All or nothing.
category: hero
hero: hero:croc-o-dill
tier: 2
difficulty: 3

objectives:
  - id: obj-1
    description: Trigger Unmatched successfully (all elements revealed)
    condition: skill:unmatched:success = true

rewards:
  - objectives_met: 1
    reward: totem:venom-idol
chain: true

curse:
  trigger: accepted and obj-1 not met by scenario-end
  effect: Erode 2 on two quadrants of the enemy's choice
  flavor: >
    The moment passed. The land remembers the hesitation.
```

---

### Tier 3

```yaml
name: contract:iron-vow
flavor: >
  The land asks everything. Heroes give it.
category: sacrifice
hero: null
tier: 3
difficulty: 5

objectives:
  - id: obj-1
    description: Survive the next wave after accepting Ravage 1
    condition: wave:survived after ravage:1:immediate
  - id: obj-2
    description: Survive with at least 2 quadrants untouched
    condition: wave:survived and desolation:quadrants-untouched >= 2

rewards:
  - objectives_met: 1
    reward: totem:TBD
  - objectives_met: 2
    reward:
      - totem:TBD
      - well-card:TBD
      - Restore 3 globally
chain: true

curse:
  trigger: accepted and obj-1 not met
  effect: Ravage 2
  flavor: >
    The vow was broken. The land does not forget.
```

---

```yaml
name: contract:flawless-wave
flavor: >
  Not one step. Not one token. Not one moment of weakness.
category: survival
hero: null
tier: 3
difficulty: 5

objectives:
  - id: obj-1
    description: >
      Complete a full wave — no enemy reaches the exit,
      no desolation tokens placed, no totem Silenced
    condition: >
      wave:completed and
      enemy:reached-exit = 0 and
      desolation:placed = 0 and
      totem:silenced = 0

rewards:
  - objectives_met: 1
    reward:
      - totem:sanctuary-idol
      - Restore 1 on all quadrants
      - well-card:TBD
chain: true

curse:
  trigger: accepted and obj-1 not met
  effect: Erode 2 on all active quadrants
  flavor: >
    Perfection was demanded. Imperfection answered.
```