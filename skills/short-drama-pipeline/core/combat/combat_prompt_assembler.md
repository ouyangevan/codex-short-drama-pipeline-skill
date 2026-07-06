# Combat Prompt Assembler

This file defines how to compress Combat Pipeline fields into `provider_execution_prompt`. The assembler must preserve visible evidence, not director reasoning. Do not output real-world fighting instruction, gore, or direct imitation of a specific IP.

## Assembly Inputs

Use these sections:

- `fight_director`: intent, combatants, objective, counter-pressure, spatial map, action chain, result state, readability plan
- `combat_beat`: beat type, screen action, anticipation, contact/collision, impact feedback, reaction, aftermath, camera logic, VFX logic, continuity out
- `impact_system`: impact level, pre-impact, contact frame, hitstop, recoil, environment feedback, sound hint, aftermath pose
- `vfx_power`: type, source, shape, behavior, color, body/environment interaction, visibility rule, start/peak/end state
- `camera_coverage`: shot type, distance, lens feel, camera motion, screen direction, subject priority, cut point, continuity in/out
- `provider_route_strategy`: provider, route class, duration, complexity, references, first/end frame plan, compression rule, unsupported controls, and fallback route
- `combat_tempo`: duration, target duration policy, key poses, action events, event distribution, traversal timing, speed curve, force-feedback beat

## High-Control Provider Prompt Assembly

Use this order:

1. Scene and spatial layout: who is where, screen direction, depth, height, and anchors.
2. Start state and anticipation: body weight, weapon/prop state, power source, visible pressure.
3. Combat tempo: target duration policy, duration, key-pose count, action-event sequence, event distribution, traversal window, and speed curve.
4. One tactical action chain: active move, counter-pressure, contact/collision.
5. Impact system: contact frame, hitstop/readability beat, recoil, environment feedback.
6. VFX power: source, attachment, peak, decay, and visibility rule.
7. Camera coverage: one primary camera behavior and cut point.
8. End state: winner/loser relation, prop/VFX state, next-shot continuity.
9. Short negative constraints: no gore, no teleporting, no hidden contact, no subtitles/UI/watermark, no IP imitation.

High-control prompts may include more detail than constrained routes, but must not include the full director analysis. If the shot includes avatar/domain/suppression, reference the power reveal or first frame explicitly and keep contact visible. A high-control route may use soft timing windows when needed, but the final prompt must still read like screen action, not a production spreadsheet.

## Constrained/Fast Provider Prompt Assembly

Use this order:

1. Starting state in one sentence.
2. Duration and compressed tempo: target ordinary combat at 2.5-3.5 seconds, key poses, action events, major traversal within the first 20-40% of the shot, and at least 60% of events before 70% of duration.
3. One main action chain with 3-5 visible events, not a single slow traversal.
4. One clear contact/collision or impact with force feedback.
5. One result state.
6. No more than four critical negative constraints.

Constrained prompts should avoid dense timestamp lists by default, but must include concrete duration and speed evidence. Prefer phrases such as "within the first second", "before the midpoint", "at contact", and "end with". If a constrained combat prompt carries too many beats for the selected duration or route capability, reject and shorten it before render. If the prompt only contains approach plus crouch/stand/turn, reject it before render. If the route fails from overload, shorten the shot, produce a key-pose still, retry with a stronger reference, split the shot, or escalate to a higher-control route.

## Action Density Assembly Rule

Before writing `provider_execution_prompt`, run this check against the selected provider's confirmed duration and control limits:

- `duration <= 2s`: at least 3 key poses.
- `duration <= 3s`: at least 4 key poses and 3 action events.
- `duration <= 4s`: at least 5 key poses and 3 action events.
- `duration >= 5s`: at least 6 key poses, 3-5 action events, and 1 force-feedback beat.
- If the shot is ordinary combat with no slow motion, emotional pause, aftermath, environment reveal, or large power reveal, target 2.5-3.5 seconds.
- At least 60% of action events must happen in the first 70% of the shot.
- The final 20-30% must be a landing pose, reaction, aftermath, or cut-ready hold, not continued travel.

The final prompt should compress those beats into a readable sentence chain. Do not list ten micro-actions if they create route overload. Combine related poses into events only when they share one target, one direction, and one result.

## 3D Guoman Assembly

Use `style_route: 3d_guoman_cinematic`.

Prioritize:

- spatial layout, parallax, low/high level, foreground/midground/background
- body weight, cloth/hair follow-through, weapon/prop state
- volumetric lighting, wet floor/cloud/dust/debris response
- avatar/domain/suppression scale anchors when present
- one camera movement that helps depth and power relation

Avoid flat face-off staging and full-screen VFX without contact.

## 2D Ink High-Dynamic Assembly

Use `style_route: 2d_ink_anime_high_impact`.

Prioritize:

- bold silhouette, graphic composition, strong line of action
- held impact frame, ink smear, brushstroke trails, speed-line rhythm
- contact frame and recoil before decorative effects
- original 2D ink martial fantasy language, not a copied work style

Avoid asking for a named show, character, or exact visual style.

## Live-Action Blockbuster Assembly

Use `style_route: live_action_blockbuster_fight`.

Prioritize:

- grounded body weight, actor reaction, editable coverage
- practical environment feedback such as dust, wall shake, water, glass, cloth, object movement
- readable camera axis, inserts, reaction shots, and end pose
- fewer abstract VFX unless the story requires them

Avoid real-world fighting instruction. Describe screen choreography, camera coverage, and PG-13 impact evidence.

