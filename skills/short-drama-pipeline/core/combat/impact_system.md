# Impact System

Impact is cinematic feedback, not injury detail. Describe readable screen evidence: contact, hitstop, recoil, environment response, sound intent, and aftermath pose.

## Impact Fields

- `pre_impact`: wind-up, lowered center of gravity, slight camera push, environmental quiet, charge-up, or threat reveal.
- `contact_frame`: one clear instant of touch/collision, crossed weapons, energy boundary, lit floor mark, or near-miss relation.
- `hitstop`: very short hold that lets the viewer read the impact.
- `recoil`: body, cloth, weapon, energy boundary, smoke, water, or debris rebound.
- `environment_feedback`: dust, broken chips, puddle ripple, sparks, light ring, cracked floor, air ripple, or shadow shift.
- `sound_hint`: foreground Foley intent such as low boom, metal ring, air pressure thump, cloth snap; do not rely on the model to generate sound.
- `aftermath_pose`: who stabilizes, who slides/backsteps/kneels/guards, and what posture proves the result.

## Impact Levels

- `level_1_contact`: light contact or probing exchange.
- `level_2_solid_hit`: clear cinematic body/short-weapon impact.
- `level_3_heavy_clash`: strong weapon, shield, wall, floor, or object feedback.
- `level_4_supernatural_burst`: energy or magic collision with readable boundaries.
- `level_5_colossal_suppression`: avatar, domain, suppression, or giant-scale pressure.

Every combat compiler output must include `impact_level` and `impact_feedback`. "Powerful attack" is invalid without visible feedback.
