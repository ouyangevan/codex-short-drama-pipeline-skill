# Combat Grammar

Combat grammar turns fictional action ideas into model-readable beat structures. It describes screen action, rhythm, contact, cinematic feedback, and continuity. It must not become real fighting instruction.

## Beat Types

- `strike_exchange`: fictional punch/kick/body exchange for screen choreography, focused on silhouette, timing, contact beat, recoil, and reaction.
- `weapon_clash`: cinematic weapon duel with attack line, parry angle, sparks, vibration, displacement, and result; do not provide real weapon-use instruction.
- `evade_and_counter`: dodge route plus counterbeat, emphasizing path, timing, camera reveal, and result.
- `pressure_lock`: one side advances or pins space while the other retreats, guards, or loses options.
- `power_release`: charge-up, energy form, release direction, collision point, and environment feedback.
- `magic_collision`: two forces meet with visible boundaries, color, deformation, push-pull, shockwave, and fading light.
- `avatar_manifestation`: dharma-body, giant form, spirit body, or colossal silhouette appears with scale reference and spatial pressure.
- `suppression_field`: gravity/realm pressure, floor pattern, air ripple, slowed motion, lowered debris, and constrained body movement.
- `domain_expansion`: environment rule change, color/space transformation, enclosure, and clear subject visibility.
- `finishing_beat`: decisive PG-13 cinematic suppression or defeat, without gore or explicit injury detail.
- `aftermath_reaction`: dust, debris, cloth, water, posture, opponent retreat, and a readable hold.

## Beat Schema

```json
{
  "beat_type": "",
  "screen_action": "",
  "tactical_meaning": "",
  "anticipation": "",
  "contact_or_collision": "",
  "impact_feedback": "",
  "reaction": "",
  "aftermath": "",
  "camera_logic": "",
  "vfx_logic": "",
  "continuity_out": ""
}
```

## Rules

- Every beat must include anticipation, contact/collision or near-miss, impact feedback, reaction, and aftermath.
- Repeated strikes may be one beat only when target, route, camera, and result are unified.
- If a beat changes target, location, power relation, prop state, VFX state, or camera coverage, split it.
