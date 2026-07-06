# Anime And 3D Donghua Fight Rules

Use this compiled cache for anime, donghua, xianxia, stylized CG, and VFX battle prompts before returning to the teaching database.

## Combat Dynamics

Every combat beat needs:

- wind-up or threat reveal
- acceleration or pressure increase
- contact, clash, near-miss, or result
- resistance before failure
- recoil, environment response, or tactical change
- aftermath or next danger

A combat beat may contain a continuous combo: repeated slashes, rapid punches, chained parries, or a flurry of blows are one beat when they share one tactical objective, one spatial route, one camera design, and one result. Split only when the combo changes target, location, tactic, power relation, prop state, or required camera coverage.

Show speed through motion blur, cloth snap, dust trails, delayed reactions, whip-pans, streaking debris, off-screen entry, sudden stop, or frame occlusion. Show power transfer through body mechanics, weapon vibration, air compression, cracked ground, shield deformation, shockwave, or object deformation.

## Action Meaning And Spatial Continuity

Before writing any fight storyboard, still prompt, or video prompt, define what every character action means to the viewer. A fight beat is invalid if it only names movement such as slide, dodge, slash, punch, connect a cable, crawl, stand, or breathe without explaining the tactical purpose, character intention, audience information, and power-state change.

Every fight sequence needs a spatial continuity map:

- fixed battlefield coordinates and safe spatial anchors
- each character's start position, end position, height level, body state, facing direction, and screen direction
- enemy facing direction, tracking direction, and reaction for every shot
- camera side and axis rule; do not cross the 180-degree axis unless a reset shot or clear spatial anchor reorients the viewer
- prop/object position, owner/handler, first visibility, and physical state before and after every shot
- carry-forward state from previous shot to next shot: posture, momentum, hand/prop state, distance, eyeline, damage, and environment change
- action meaning: what the viewer learns or feels from the movement, not just what moves

Every 3-5 second combat shot should usually contain at least two readable action components: the protagonist's tactic and the opponent's counter-pressure, plus a visible result state. Static posing, unmotivated breathing, or one isolated action without enemy response is not enough for a premium fight beat.

## Fight Final Mode

Use `fight_final` for final-level battle shots, key contact shots, high-value xianxia/donghua/live-action-style combat, or any shot where action quality depends on contact clarity, opponent reaction, prop continuity, VFX attachment, and camera/action synchronization.

`fight_final` is a compiler mode, not a prose style. It has three layers:

- `director_layer`: story purpose, emotion, power relation, style profile, and why the shot exists.
- `action_graph_layer`: spatial setup, start pose, one tactical objective, primary action, contact target, opponent reaction, end state, VFX cues, prop states, and continuity carry-forward.
- `execution_layer`: compressed provider execution prompt, negative constraints, API params, asset bindings, and QC expectations.

Priority order:

1. Provider hard constraints.
2. Shot readability and spatial continuity.
3. One tactical objective per shot.
4. Clear visible contact and reaction.
5. Character, prop, and VFX continuity.
6. Camera behavior.
7. Style polish.
8. Audio only when confirmed useful.

Required Combat Pipeline fields:

- `style_route`: `3d_guoman_cinematic`, `2d_ink_anime_high_impact`, or `live_action_blockbuster_fight`.
- `shot_intent`: what the viewer should understand or feel after this shot.
- `spatial_setup`: screen left/right, depth, height, facing direction, distance, axis, and safe anchors.
- `start_pose`: body state, weight, grip, weapon/prop position, gaze, and readiness.
- `primary_action`: one tactical objective; repeated slashes/punches are allowed only when they share one target, route, camera design, and result.
- `contact_target`: exact first visible contact point or near-miss relationship.
- `reaction`: opponent/environment response after contact, with force direction.
- `end_state`: final posture, power relation, prop state, damage/destruction state, and next-shot handoff.
- `camera_behavior`: one primary camera behavior only.
- `lighting`: source, direction, color temperature, reflections, shadows, and VFX light logic.
- `props_assets`: character, scene, prop, start frame, end frame, reference video, and reference audio bindings by role and order.
- `vfx_cues`: when the VFX appears, what it attaches to, how long it lasts, whether it reveals or occludes action, and its environment response.
- `negative_constraints`: short blockers tied to known failure modes.
- `api_params`: model, route, duration, ratio/aspect_ratio, resolution, seed, generate_audio, return_last_frame, watermark, callback, and verified provider fields.

Automatic split rule: split into multiple shots if a proposed shot contains more than one primary tactical objective, more than two visible contact events, more than one major camera behavior, or more than one major VFX state shift. Do not hide an overloaded fight beat inside a longer prompt.

Failure repair order:

1. `action_overload`
2. `missing_contact_visibility`
3. `unclear_spatial_axis`
4. `reaction_not_bound_to_contact`
5. `vfx_occludes_action`
6. `camera_competes_with_action`
7. `prop_binding_missing`
8. `style_conflict`
9. `model_route_too_weak`

When repairing a fight prompt, keep the approved story, identity, scene, and successful control layers. Change one primary variable at a time and output `failure_reason`, `what_to_remove`, `what_to_keep`, `revised_shot_graph`, `revised_provider_execution_prompt`, and `revised_api_params`.

## Anime Battle Direction

Top-tier anime/donghua battles require `04E_anime_battle_direction.md` before prompt writing:

- animation timing chart
- key pose sheet
- character combat style
- combo chain
- anime FX bible
- anime editing grammar
- battle-space map
- layered generation plan

## 3D Donghua Action Layout

Top-tier 3D donghua / 3D anime-style battles require `04F_3d_donghua_action_layout.md` before prompt writing:

- layout blocking map
- camera and character trajectories
- animation mechanics and root motion
- contact and IK notes
- FX-light-compositing binding
- battle asset state pack
- action readability QC

If layout, mechanics, FX/compositing, and readability cannot fit in one generation, split into layout stills, key-pose stills, short action clips, impact inserts, FX plates, aftermath, and reaction shots.

For finished action output, generate multiple planned shots or storyboard panels as separate clips and stitch them in editing. Do not upload a full multi-panel storyboard grid as the reference for one complex video generation.

## Readability

Do not hide unreadable action behind fast cuts, bright FX, camera shake, or heavy motion blur. The silhouette, attack line, anticipation, impact frame or hitstop, contact/result clarity, and winner/loser state must read.

