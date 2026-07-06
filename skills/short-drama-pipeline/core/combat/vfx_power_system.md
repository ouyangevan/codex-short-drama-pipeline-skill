# VFX Power System

VFX must support action readability. Do not use generic "epic energy" as a substitute for physical/contact logic.

## VFX Layer

```json
{
  "vfx_type": "none | aura | weapon_energy | impact_wave | magic_collision | avatar_manifestation | suppression_field | domain_expansion",
  "source": "",
  "shape_language": "",
  "motion_behavior": "",
  "color_temperature": "",
  "interaction_with_body": "",
  "interaction_with_environment": "",
  "visibility_rule": "VFX must support action readability, not hide contact frame",
  "start_state": "",
  "peak_state": "",
  "end_state": ""
}
```

## Type Rules

- `aura`: stays close to the body; avoid full-screen glow.
- `weapon_energy`: follows the weapon path while preserving weapon silhouette.
- `impact_wave`: expands from the contact point and moves dust, water, debris, cloth, or smoke.
- `magic_collision`: two forces have edges, pressure, deformation, push-pull, and decay; not only a big explosion.
- `avatar_manifestation`: show shadow or outline first, then partial form, then complete scale; include human/environment scale reference.
- `suppression_field`: show space becoming heavy through floor marks, downward air ripple, lowered debris, slowed cloth, and constrained posture.
- `domain_expansion`: environment rules change through color, light, background geometry, or enclosure, while subjects remain clear.
