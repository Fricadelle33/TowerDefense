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
