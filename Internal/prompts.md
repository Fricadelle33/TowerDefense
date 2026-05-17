# Prompt

## Market Supervisor

### Template-supervisor

Run [market-supervisor] on [TARGET_FILE.md].
Isolate context: load ONLY [TARGET_FILE.md] and [Database/SSOT_rules.md].
Evaluate mechanics against <failure_triggers> using <evaluation_lenses>.
Output ONLY:

1. Evaluation table [Mechanic | Trigger | Severity].
2. Patched YAML blocks for CRITICAL failures.

Zero prose. Zero flavor text.

### Example-supervisor

> Use Database\0_Basics\design-guidelines.md

===

## Adversial GM

### Template-adv

Run [adversarial-gm] on [TARGET_SCENARIO.yaml].
Isolate context: load ONLY [TARGET_SCENARIO.yaml] and [Database/SSOT_rules.md].
Execute enemy turns maximizing <priorities> using <heuristics>.
Output ONLY:

1. Evaluation table [Turn | Enemy | Action | Board Delta | Trigger Flag].

Zero prose. Zero flavor text.

### Example-adv

> Use Database\0_Basics\design-guidelines.md

===

## Creative Player

### Template-creative

Run [creative-player] on [TARGET_HERO_DECK.yaml].
Isolate context: load ONLY [TARGET_HERO_DECK.yaml] and [Database/SSOT_rules.md].
Force-test <test_patterns> against <priorities>.
Output ONLY:

1. Evaluation table [Exploit/Combo | Mechanism | Actual vs Expected Ceiling | Trigger Flag].
2. Patched YAML block for CRITICAL failures.
Zero prose. Zero flavor text.

### Example-creative

> Use Database\0_Basics\design-guidelines.md

===

## Rotating

### Template-rotating

Run [rotating-player] using <persona:ID> on [TARGET_SCENARIO.yaml].
Isolate context: load ONLY [TARGET_SCENARIO.yaml] and [Database/SSOT_rules.md].
Simulate session constrained by persona <logic> and <focus>.
Output ONLY:

1. Evaluation table [Turn | Decision | Emotional Reaction | Trigger Flag].
Zero prose. Zero flavor text.

### Example-rotating

> Use Database\0_Basics\design-guidelines.md

===

## Strict Validator

### Template-strict-validator

Run [strict-validator] on [TARGET_CARD_FILE.yaml].
Isolate context: load ONLY [TARGET_CARD_FILE.yaml] and [Database/effects-vocabulary.md].
Execute mechanical linting against <lint_rules>.
Output ONLY:

1. Evaluation table [Card Name | Violation | Proposed Fix].
2. Patched YAML blocks for ALL flagged violations.
Zero prose. Zero flavor text.

### Example-strict-validator

Run [strict-validator] on [Database\1_Cards\Heroes\0_Croc\hero-croc-burrow.md] and [Database\1_Cards\Heroes\0_Croc\hero-croc-cards.md]

Isolate context: load ONLY:

- [Database\1_Cards\Actions\action-template.md]
- [Database\1_Cards\Towers\tower-template.md]
- [Database\1_Cards\Totems\totem-template.md]
- [Database\1_Cards\effects-vocabulary.md]

Execute mechanical linting against <lint_rules>.
Output ONLY:

1. Evaluation table [Card Name | Violation | Proposed Fix].
2. Patched YAML blocks for ALL flagged violations.
Zero prose. Zero flavor text.
