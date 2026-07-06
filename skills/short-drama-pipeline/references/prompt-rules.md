# Prompt Rules

## Prompt Delivery Gate

Do not emit generation-ready still prompts or video prompts unless the current stage has a passing `knowledge_gate` and a passing or non-applicable `asset_gate`.

- Character-asset prompts are incomplete unless they produce the full pack: four-view, expression, marker/detail, and close-up references for each core character.
- Scene-asset prompts are incomplete unless they produce the full pack: 720-degree/multi-angle references, key camera positions, state variations, and prop close-ups for each core scene.
- Shot prompts are incomplete unless they bind references by role and include start/end-frame logic, continuity state, physical-logic check, and sound layer when the selected route supports native dialogue/Foley.
- Shot prompts are incomplete unless they include a frame phase plan that separates starting frame, storyboard/reference frame, and ending frame by causal action phase.
- If the prompt-source compliance check fails, set `allowed_output` to `blocked_report_only`; do not send the prompt to a model and do not present it as ready.

Knowledge source rule:

- Use `knowledge_compiled/prompt_rules.md` plus the relevant compiled cache files before searching raw teaching material.
- Search raw or external teaching material only on cache miss, conflict, new material, user-requested relearning, or missing rule coverage.
- In `prompt_test_mode=true`, prompts are `draft_only_prompt_test`; do not call them generation-ready or production deliverables until normal gates pass.

## Professional Production Gate

Do not write generation-ready prompts from script and storyboard alone. For professional-level video, prompts must inherit constraints from these episode-level artifacts:

- `series_engine`: viewing promise, long-arc desire, per-episode payoff mechanism, pressure escalation, secret/evidence/payoff ledger, cluster reversal plan, and audience knowledge state.
- `director_treatment`: overall visual promise, emotional curve, camera grammar, rhythm, color/light route, and sound route.
- `reference_board`: selected reference directions and explicit non-copy rules.
- `theme_and_mise_en_scene`: theme statement, visual motifs, power-space grammar, psychology-to-space/light conversion, composition motif/reversal, and forbidden cheap emotion shortcuts.
- `prop_and_evidence_ledger`: proof objects, repeated props, ownership/handler, first appearance, payoff shot, physical state changes, closeups, text/post plan, and continuity risks.
- `coverage_plan`: master, clean singles, over-shoulders, reactions, inserts, proof/object shots, transitions, atmosphere, and safety shots.
- `blocking_plan`: actor movement paths, power positions, distance changes, eye-lines, occlusion, and prop handoff.
- `performance_direction`: subtext, line intention, pause, breath, gaze, micro-expression, restraint/explosion point, reaction timing, scene objective, obstacle, tactic, beat changes, playable action verbs, emotional temperature, and reaction priority.
- `lens_camera_language`: camera height, distance, lens feeling, compression, handheld/stabilized/tracking/drone feeling, and depth of field.
- `cinematography_bible`: aspect ratio/framing, lens package, focal length rule, camera support, camera height power rule, depth strategy, exposure/contrast texture, movement restrictions, and shot-family continuity.
- `light_color_script`: color arc, light source logic, contrast, warm/cold shift, shadow, rim/back light, and reveal darkness.
- `production_design_texture`: costume, makeup, hair, material, wear, class/status symbols, prop symbolism, and set dressing.
- `editing_rhythm_map`: cut rhythm, hold points, reaction duration, proof insert timing, transition logic, silence beats, and ending hook cut.
- `sound_director_layer`: voice performance, Foley priority, silence, music entry/exit, riser/hit points, sound bridges, and foreground-only native-audio rules.
- `previs_animatic_plan`: rough timeline, dialogue-picture fit, action continuity check, edit rhythm, music/Foley cue map, missing inserts, generation risk, and animatic decision.
- `audience_comprehension_map`: every-3-second viewer knowledge, shot information delta, viewer question track, clue/emotion split, misdirection clarity, silent-watch readability, and reversal setup/payoff.

If any required artifact is missing for a serious production run, label the package `not_professional_ready` and create the missing artifact before prompt writing.

## Narrative Engine And Audience Clarity Gate

Do not write generation-ready prompts that only make a shot look good while weakening the series engine or audience comprehension.

Before prompt writing, check:

- The shot serves the `viewing_promise` and current episode payoff mechanism.
- Any secret, clue, evidence, or prop in the prompt matches the `secret_evidence_payoff_ledger` and `03C_prop_and_evidence_ledger.md`.
- The prompt's blocking, light, prop use, and composition express the current `theme_and_mise_en_scene` rule.
- The performance note contains a playable tactic and beat change when the character is actively trying to win, hide, test, expose, seduce, threaten, protect, or escape.
- The shot has a clear information delta and viewer question from `04I_audience_comprehension_map.md`.
- The shot remains understandable on silent autoplay through action, expression, prop close-up, staging, or post-production text/caption plan.

If a prompt adds beauty but removes proof clarity, reverses prop state, breaks audience knowledge, hides the payoff object, or makes the scene unreadable without audio, it is not generation-ready.

## Cinematography Bible Gate

Do not rely on one-off lens phrases inside individual prompts. Before professional prompt writing, create or inherit `04G_cinematography_bible.md`.

The prompt pack must obey:

- `aspect_ratio_and_framing`: the target frame, safe area, headroom, negative space, and mobile readability.
- `lens_package`: which lens families exist in this episode and what each one is for.
- `focal_length_rules`: how lens feeling changes by character status, power state, intimacy, scale, or story beat.
- `camera_support_rules`: when to use locked-off, handheld, stabilized, tracking, crane/drone-like, orbit, push/pull, or whip-pan, and when each is forbidden.
- `camera_height_power_rules`: how eye level, low angle, high angle, overhead, ground level, and shoulder level express pressure, vulnerability, scale, status, or intimacy.
- `depth_of_field_strategy`: when to use deep focus, shallow focus, rack focus, foreground occlusion, or reflection.
- `exposure_contrast_texture`: how source light, contrast, silhouette, rim/back light, shadow density, flare, reflection, and practical light support the scene.
- `movement_restrictions`: moves that must not be repeated mechanically.
- `shot_family_continuity`: the recurring camera grammar for protagonist, antagonist, romance, humiliation, power entrance, action, proof inserts, and cliffhangers.

If a prompt says "cinematic lens", "slow push-in", "shallow depth of field", or "handheld" without inheriting this camera system, it is not professional-ready.

## Previs And Animatic Gate

Before professional prompt writing, create or inherit `04H_previs_animatic_plan.md`. This is the rough-cut check before paying for image/video generation.

The prompt pack must obey:

- `rough_timeline`: shot order, estimated duration, hold points, speed changes, and total duration.
- `dialogue_picture_fit`: whether each line is on-screen, off-screen, over reaction, over insert, or split across shots.
- `action_continuity_check`: whether motion, screen direction, prop state, body position, eyeline, and aftermath carry across cuts.
- `edit_rhythm_map`: where the scene holds, cuts fast, uses reaction, insert, proof shot, silence, music hit, or hard cut.
- `music_foley_cue_map`: where dialogue, visible-source foreground Foley, silence, riser/hit, and music phrase points land.
- `missing_insert_list`: extra hands, objects, reactions, transition shots, atmosphere, proof shots, safety shots, and cutaways needed before generation.
- `generation_risk_map`: high-risk shots, likely model failures, split/regenerate route, backup insert plan, and max retry budget.
- `animatic_decision`: pass, revise storyboard, split shot, add insert, shorten dialogue, change camera, regenerate asset, or block.

If dialogue is too long for the usable picture, an action phase cannot cut cleanly, music/Foley would stop abruptly, or a high-risk shot has no backup insert plan, do not generate. Revise storyboard, timing, or prompt structure first.

## Cinematic Intent Gate

Do not fill `shot size`, `composition`, `camera movement`, or `screen time` mechanically. Before writing any generation-ready prompt, write a visual-director pass that answers:

- `visual_intent`: what should the viewer feel in this shot: awe, pressure, humiliation, intimacy, danger, scale, revelation, speed, or impact?
- `scale_class`: intimate close-up, room-scale conflict, street-scale action, palace/sect-scale scene, mountain/cloud-sea spectacle, colossal-form/VFX spectacle, or battle-impact spectacle.
- `composition_hierarchy`: foreground, midground, background, dominant shape, negative space, light direction, and where the eye should travel.
- `camera_motivation`: why this camera moves; what new information, power relation, or emotional pressure is revealed by the move?
- `reveal_path`: near-to-far, low-to-high, behind-to-front, shadow-to-form, silence-to-impact, or small-human-to-colossal-scale.
- `environment_response`: clouds, robes, dust, water, floor cracks, mountain mist, banners, weapon light, particles, or shockwaves that prove the scale.

If the prompt only says characters stand left/right, hold poses, release energy, and collide in the center, it has failed the cinematic intent gate for any requested epic, fantasy, xianxia, Eastern-aesthetic, or VFX battle shot.

For large Eastern-aesthetic scenes, use scale and reveal language, for example:

`å®å¤§è¿œæ™¯ä¿¯æ‹ï¼Œé•œå¤´ä»Žè§’è‰²è¡£è¢‚å’Œå±±å·…çŸ³é˜¶è¿‘å¤„ç¼“æ…¢åŽæ‹‰å¹¶å‡é«˜ï¼Œç”±è¿‘åˆ°è¿œé€æ¸å±•å¼€äº‘æµ·ã€ç¾¤å³°ã€è¿œå¤„æ‚¬æµ®å±±é—¨å’Œå¤©å…‰ï¼Œå‰æ™¯è¡£è¢‚è¢«é£ŽæŽ€åŠ¨ï¼Œä¸­æ™¯è§’è‰²ç«‹äºŽå±±å·…è¾¹ç¼˜ï¼ŒèƒŒæ™¯äº‘å±‚ç¿»æ¶Œå½¢æˆå·¨å¤§çš„ç©ºé—´çºµæ·±ã€‚`

For colossal-form pressure, make the human small and the form dominant:

`ä½Žæœºä½ä»°æ‹æŽ¨è¿›ï¼Œäººç‰©åªå ç”»é¢ä¸‹æ–¹å¾ˆå°æ¯”ä¾‹ï¼Œèº«åŽå·¨å¤§çš„åŠé€æ˜Žæ³•ç›¸ä»Žäº‘å±‚å’Œç¬¦æ–‡å…‰æŸ±ä¸­ç¼“æ…¢æ˜¾å½¢ï¼Œæ³•ç›¸è‚©éƒ¨é®ä½åŠç‰‡å¤©ç©ºï¼Œé•œå¤´è½»å¾®éœ‡é¢¤å¹¶å‘ä¸Šå€¾æ–œï¼Œé˜´å½±åŽ‹è¿‡åœ°é¢ï¼Œç¢ŽçŸ³å’Œè¡£æ‘†è¢«æ°”æµªå‘é•œå¤´æ–¹å‘å·èµ·ã€‚`

For high-impact VFX battles, do not default to one flat two-person face-off. Split or design the beat as:

1. scale reveal: extreme wide or high-angle shot showing battlefield, distance, sky/ground layers, and power imbalance
2. build-up: over-shoulder or low-angle shot with energy changing the environment
3. trajectory: wide shot with foreground objects streaking past lens and two forces moving through depth, not only left-to-right
4. impact: one clear collision moment with shockwave, parallax, debris, light falloff, and character reaction
5. aftermath: silence, dust clearing, cracked ground, changed posture, or reveal hook

Use negative direction when needed: `no flat stage-like two-person duel, no static equal left-right composition, no simple beam collision, no medium-shot pose-only spell casting, no empty background, no ordinary standing face-off`.

## Professional Direction Gate

Every shot in every genre needs professional camera, transition, and light design. This is not limited to combat, fantasy, spectacle, or VFX scenes.

Before writing any storyboard shot, still prompt, or video prompt, define:

- `dramatic_function`: what the shot does for the scene: reveal, conceal, pressure, intimacy, humiliation, suspicion, reversal, comedy beat, power shift, grief, temptation, proof, or cliffhanger.
- `viewer_attention`: where the viewer's eye should go first, second, and last.
- `camera_motivation`: why the camera moves or stays still; what information, emotion, or power relation changes because of that choice.
- `movement_design`: the exact camera behavior and rhythm: slow push-in, creeping lateral slide, handheld follow, locked-off pressure, rack focus, whip pan, pull-back reveal, orbit, over-shoulder drift, foreground wipe, or motivated cut.
- `transition_design`: how this shot enters and exits: match cut, action cut, eye-line cut, reaction cut, object wipe, sound bridge, light wipe, door/cloth/foreground occlusion, smash cut, J-cut, L-cut, or deliberate hard cut.
- `lighting_design`: source, direction, contrast, color temperature, shadow shape, practical lights, rim light, silhouette, reflection, flare, underlight, backlight, or darkness reveal.
- `depth_design`: foreground occlusion, midground action, background information, lens feeling, depth of field, reflection, window/door frame, corridor depth, crowd layer, or negative space.
- `rhythm`: how long the viewer should sit in tension before the reveal, line, action, or reaction.

If a shot can be summarized as "medium shot, character speaks, camera slowly pushes in" without changing the viewer's feeling or information, it has failed the professional direction gate.

Genre-specific direction examples:

- Power reversal / face-slap: start with the aggressor dominating foreground or higher frame position, cut to the protagonist in controlled stillness, use a slow push-in or locked-off frame as the room quiets, then a reaction cut or object insert reveals proof.
- Suspense: use partial occlusion, shallow focus, corridor depth, slow lateral slide, reflected information, off-screen sound bridge, low-key light, and delayed reveal instead of plainly showing everything.
- Romance / emotional pull: use close distance, soft side/back light, shallow depth, small hand/eye/breath details, slow orbit or micro push-in, and a held reaction before dialogue.
- Family or workplace humiliation: use wider spatial shots to show social pressure, foreground backs/shoulders blocking the target, cold overhead or side light, then cut to a tighter reaction when the insult lands.
- Comedy or irony: use static framing, delayed reaction, sudden rack focus, object insert, or smash cut; do not over-dramatize every beat.
- Luxury / power entrance: use low-angle or backlit entrance, foreground silhouettes, practical lights, reflections, slow reveal through door/curtain/elevator, and reaction cuts that show status changing in the room.

## Combat Dynamics Gate

Every combat scene needs combat dynamics, not only action labels. This applies to hand-to-hand fights, weapon fights, spell fights, supernatural battles, monster pressure, chase attacks, ambushes, and impact shots.

Combat shots must use the Combat Pipeline before ordinary video prompt writing. Produce `combat_prompt_compiler_output.json` or an equivalent object validated against `schemas/combat_prompt_compiler_output.schema.json`. Do not go directly from "fight idea" to a prose video prompt.

Before writing a combat prompt, define:

- `pressure`: how the camera, composition, blocking, lens, scale, light, and screen space make a character feel oppressive or make another character feel visually crushed. It is not only "who is winning". Show it with low-angle dominance, foreground body blocking, frame compression, looming silhouettes, the weaker character squeezed to the edge/bottom of frame, negative space closing in, slow push-in, shadow falling over the target, or a dominant form occupying most of the frame.
- `tension`: how the camera, composition, timing, and movement make an attack or action feel stretched, coiled, and about to release. It is not only "what is about to break". Show it with held pause before impact, diagonal attack lines, weapon/hand entering extreme foreground, shallow-focus distance compression, frame-edge threat, occluded danger, slow push before sudden motion, whip-pan anticipation, body coiling, cloth/air pulling toward the force, or a near-contact gap that the viewer can feel closing.
- `speed`: what visual cue proves speed: motion blur, cloth snap, dust trail, delayed reaction, whip-pan, streaking debris, sudden stop, or off-screen-to-on-screen entry?
- `power`: where does the force come from and how does it travel through body, weapon, energy, ground, air, or object?
- `impact`: the exact contact or result moment: body recoil, weapon spark, shield crack, ground fracture, splash, shockwave, stumble, slammed table, shattered glass, or dust burst.
- `resistance`: how the target or environment resists the force before failing; a hit without resistance feels weightless.
- `aftermath`: what changed after the strike: posture, distance, damage, silence, dust clearing, new fear, exposed weakness, or reversal.

Combat prompt structure:

1. wind-up or threat reveal
2. acceleration, visual pressure increase, or visual tension release
3. contact / clash / near-miss
4. recoil, environmental response, or tactical change
5. reaction or next danger

For close combat, prioritize body mechanics and camera rhythm: planted foot, shoulder rotation, hip turn, guarded face, blocked strike, delayed recoil, breath, cloth snap, handheld shake, and fast cut to reaction.

For weapon combat, show reach, line of attack, parry angle, sparks, blade/weapon vibration, grip pressure, footwork, and follow-through. Avoid vague "they fight fiercely" wording.

For supernatural or VFX combat, show scale plus force transfer: energy compresses the air, ground cracks before release, clouds or smoke are pulled toward the source, the target's shield bends under pressure, impact creates a shockwave and delayed debris fall.

For chase/ambush combat, show speed through occlusion and reveal: attacker crosses foreground, camera whip-pans, target enters frame late, background streaks, obstacle breaks, or the strike lands before the viewer fully catches up.

If a combat prompt lacks visual pressure, visual tension, speed cue, power transfer, impact result, resistance, and aftermath, it is not generation-ready. Pressure and tension must be expressed through camera/composition/timing, not only through story labels.

Safety and originality:

- Keep combat as fictional film/anime screen choreography.
- Do not output real-world fighting instruction, real injury detail, gore, or practical harm guidance.
- Do not request direct imitation of a specific IP, character, shot, line, or identifiable work style. Use original type language such as `3d_guoman_cinematic`, `2d_ink_anime_high_impact`, or `live_action_blockbuster_fight`.

## Anime Battle Direction Gate

For top-tier anime battle, donghua/anime-style combat, xianxia anime action, stylized 2D/2.5D/3D anime fights, or any fight where the target is premium animation impact, do not write prompts from ordinary combat dynamics alone.

Before still prompts or video prompts, create or inherit `04E_anime_battle_direction.md` with:

- `animation_timing_chart`: anticipation, hold, acceleration, impact frame, recoil, follow-through, recovery, smear/impact-frame hold if used.
- `key_pose_sheet`: start pose, wind-up pose, burst pose, contact pose, hit reaction pose, aftermath pose, readable silhouette, line of action, and limb/weapon direction.
- `character_combat_style`: each fighter's movement personality, rhythm, range, attack route, defense habit, signature weapon/energy shape, and weakness.
- `combo_chain`: where this shot sits in probe, evade, counter, guard break, chase, reversal, finisher, interruption, or cliffhanger.
- `anime_fx_bible`: fixed shape/color/edge/trail rules for aura, sword energy, magic circles, smoke, dust, debris, sparks, shockwave, speed lines, lightning, fire, water, and environment response.
- `anime_editing_grammar`: stillness-to-burst, cut-in, reaction cut, impact frame, speed-line wipe, black-frame hit, match-on-action, foreground wipe, fast insert, silence hold, and hold/release rhythm.
- `battle_space_map`: character position, distance, height, ground/air state, axis, camera side, attack direction, retreat path, obstacles, destructible terrain, and terrain changes after the exchange.
- `action_meaning_map`: for each character action, state tactical purpose, character intention, opponent counter-pressure, what the viewer learns or feels, and how the power relation changes.
- `spatial_continuity_map`: fixed battlefield coordinates, start/end position, facing direction, screen direction, body state, prop state, camera side, 180-degree axis rule, and carry-forward state from the previous and next shot.
- `layered_generation_plan`: layout, key pose, action timing, FX, camera, impact, sound, and continuity layers.

Anime battle prompt structure:

1. layout, battle-space state, facing direction, and axis rule
2. key pose / silhouette target
3. animation timing chart
4. action beat, action meaning, and combo-chain role
5. camera and anime editing grammar
6. FX layer and environment response
7. impact frame / recoil / aftermath
8. foreground Foley and silence/music handoff plan
9. continuity state for the next shot: position, body state, facing direction, screen direction, prop state, and enemy reaction

If the video model cannot carry all layers in one generation, split the shot into layout/key-pose stills, short action clips, impact inserts, reaction shots, and FX plates. Do not compress a full combo, camera move, pose change, FX explosion, dialogue, and environment destruction into one short prompt.

## 3D Donghua Action Layout Gate

For top-tier 3D å›½æ¼«, 3D anime-style battle, cinematic xianxia 3D combat, stylized CG martial action, or any fight where the target depends on 3D layout, animation mechanics, FX-light integration, and action readability, do not write prompts from `04E_anime_battle_direction.md` alone.

Before still prompts or video prompts, create or inherit `04F_3d_donghua_action_layout.md` with:

- `layout_blocking_map`: terrain coordinates, character start/end positions, height levels, camera side, screen direction, axis rule, reset points, and safe spatial anchors.
- `camera_character_trajectory`: camera path, character path, parallax layers, foreground/midground/background crossing, occlusion/reveal points, speed changes, and camera stop/readability points.
- `action_meaning_and_viewer_delta`: why each character moves, what tactic it expresses, what the opponent does in response, what the viewer understands, and how the shot changes the power relation.
- `animation_mechanics`: center of gravity, root motion, foot planting, hip/shoulder rotation, weapon arc, landing buffer, recoil, follow-through, balance recovery, and secondary motion.
- `contact_and_ik_notes`: hand/weapon grip, foot-ground contact, collision point, shield/weapon contact, body penetration risks, prop scale, left/right limb control, and crop/occlusion plan for risky contact.
- `fx_light_compositing_binding`: how FX casts light, creates shadow, reflects on costume/skin/ground, obscures or reveals silhouette, and layers in foreground/background.
- `battle_asset_state_pack`: combat outfit, weapon, energy form, damage/dirty states, facial strain, scene destruction, debris, and before/mid/after environment variants.
- `action_readability_qc`: silhouette, attack line, anticipation, impact frame/hitstop, contact/result clarity, motion-blur limits, camera-shake limits, and clear winner/loser state.

3D donghua prompt structure:

1. layout and spatial anchor
2. character/camera trajectory
3. animation mechanics and root motion
4. contact/IK and risky-body-part handling
5. FX-light-compositing interaction
6. battle asset state before and after
7. action readability QC and split/regenerate plan

If the model cannot carry layout, mechanics, FX/compositing, and readability in one generation, split into layout stills, key-pose stills, short action clips, impact inserts, FX plates, and aftermath/reaction shots. Do not hide unreadable action behind motion blur, camera shake, bright FX, or fast cutting.

A continuous combo such as repeated slashes, rapid punches, chained parries, or a flurry of blows can be one performable action beat when it shares one tactical objective, one spatial route, one camera design, and one result. Do not split readable continuous combos merely because several hits occur; split only when the combo changes target, location, tactic, power relation, prop state, or required camera coverage.

Do not write fight prompts from attractive storyboard poses alone. Before prompt wording, prove the shot's start state can physically inherit from the previous shot and its end state can physically cause the next shot. If a character slides behind an enemy, the next shot must preserve that behind/side relation unless a visible turn, cutaway, reset shot, or match-on-action transition reorients the viewer.

## Fight Final Mode Gate

Use `fight_final` for final-level battle shots, key contact shots, high-value hero moments, complex supernatural combat, or any fight where the user expects premium action rather than a draft.

`fight_final` output is a prompt compiler artifact, not a paragraph. It must separate:

1. `director_layer`: story purpose, emotion, power relation, style profile, and why this shot exists.
2. `action_graph_layer`: spatial setup, start pose, tactical objective, primary action, contact target, reaction, end state, prop states, and VFX cues.
3. `execution_layer`: short provider execution prompt, negative constraints, asset bindings, API params, and QC expectations.

Required fields:

- `style_route`: `3d_guoman_cinematic`, `2d_ink_anime_high_impact`, or `live_action_blockbuster_fight`
- `shot_intent`: what the viewer should understand or feel
- `spatial_setup`: screen position, depth, height, facing direction, distance, axis, and anchors
- `start_pose`: body weight, grip, weapon/prop position, gaze, readiness
- `primary_action`: one tactical objective; repeated strikes count as one only when route, target, camera, and result stay unified
- `contact_target`: the first visible contact point or near-miss relation
- `reaction`: opponent/environment response after contact, with force direction
- `end_state`: final posture, power relation, prop state, damage/destruction state, and next-shot handoff
- `camera_behavior`: one primary camera behavior
- `lighting`: source, direction, color, reflection, shadow, VFX light logic
- `props_assets`: role/order bindings for character, scene, prop, start frame, end frame, reference video, and reference audio
- `vfx_cues`: trigger, attachment, duration, synchronization, environment response, and occlusion rule
- `negative_constraints`: short, failure-specific constraints
- `api_params`: provider-confirmed model, route, duration, ratio/aspect ratio, resolution, seed, audio, return_last_frame, watermark, callback, and quality fields

Automatic split rule: split the shot before prompt writing if it has more than one tactical objective, more than two visible contact events, more than one major camera behavior, or more than one major VFX state shift.

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

A repair must output `failure_reason`, `what_to_remove`, `what_to_keep`, `revised_shot_graph`, `revised_provider_execution_prompt`, and `revised_api_params`. Preserve successful story, identity, scene, and control layers; change one primary variable per retry.

## Still Image Prompt

Formula:

`style + subject + character appearance/clothes/action + scene/background + shot/composition + light + quality`

Negative prompt:

`low resolution, deformed body, bad fingers, face collapse, wrong proportion, dirty background, text, watermark, subtitles, irrelevant modern elements, copyrighted character, celebrity likeness`

Rules:

- Before submitting any still-image prompt, run a prompt-source compliance check: re-open the relevant database and skill rules, compare the prompt against character DNA, scene anchors, reference binding, style consistency, physical logic, and QC blockers, then revise before generation if any item fails.
- Before writing shot stills, create a frame phase plan. The starting-frame prompt, storyboard/reference-frame prompt, and ending-frame prompt must be three separate prompts unless the shot is intentionally static.
- Starting frame prompt must show pre-action setup: the cause has not yet visibly completed. Example: for a glass slipping shot, the glass is still in the character's hand with fingers loosening.
- Storyboard/reference frame prompt must show the representative middle phase or composition guide. Example: the glass is halfway through the fall, motion direction clear, source hand above, target floor/table below.
- Ending frame prompt must show result/aftermath. Example: broken glass shards and spilled liquid on the floor/table, with character reaction or aftermath state if needed.
- Never use a mid-action storyboard/reference frame as the starting frame for the video. Never use an ending/result frame as the starting frame for the cause.
- If the physical gap between starting and ending frames is too large, add intermediate frame prompts or split the shot.
- A full multi-panel storyboard grid is for planning, review, and selecting panels. Do not upload the whole grid as the video reference for one generation. Crop the intended panel or create a dedicated single-panel/frame reference for each generated clip. If no upscale/repair route is configured, do not block generation on upscale; use the cropped panel after basic visual QC.
- repeat character DNA, not only the character name
- scene details must match the scene bible
- do not add unscripted props or events
- no subtitles, text, UI, or watermark
- if a still-image prompt is blocked or returns unusable output, retry directly with safer/compliant visual wording while preserving approved story causality, character DNA, scene anchors, prop facts, and the image purpose label
- record the failed wording/problem, changed prompt/visual handling, retry count, output file, and QC result; after completion, explain what went wrong and what changed

Character assets:

- Core characters need four-view sheets, expression sheets, marker details, and close-up references.
- Provider-profile update: six-view character sheets can be used as an upgrade when the selected route supports them, but do not lower the existing minimum below four-view sheets.
- The three-view plus large face close-up layout found in the new teaching material is a supplemental layout only, not a replacement for four-view sheets unless the user explicitly approves that downgrade.
- Four-view prompts must specify same fictional character, same outfit, same hair, same body proportion, front/left/right/back.
- Expression prompts must specify same fictional character, same outfit and hair, 6-8 expressions, face consistency.
- Base character images should be front-standing, clean, neutral or white background, no UI/text, and no unrelated props.
- When turning a base character design into an action or story frame, keep the character DNA but remove constraints that no longer apply, such as pure white background, front view, standing pose, or arms naturally lowered.
- Use side, back, detail, or expression references only when the shot needs that information. Extra references can reduce consistency.

Scene assets:

- Core scenes need 720-degree/multi-angle spatial references before moving-camera shots.
- Scene prompts must preserve fixed anchors: entrance, table, screen, windows/walls, floor material, light sources.
- Generate state variations separately: before conflict, reversal, aftermath.

Prop assets:

- Repeated props need an independent prop image and at least one character-bound reference that fixes scale, grip, wearing position, or use state.
- Do not rely only on text like "5cm" or "small cup" when the prop repeatedly appears across shots.
- Keep base character references clean; add story props through shot-specific bound references.

Reference binding:

- Multi-reference prompts must map every uploaded asset by order and purpose before action text: image 1 is character A, image 2 is character B, image 3 is the scene, image 4 is the prop.
- For providers that use inline asset handles such as `@image1`, map every uploaded asset before action text: `@image1 is character A`, `@image2 is character B`, `@image3 is the scene`, `@image4 is the prop`, `@video1 is action/camera reference only`, `@audio1 is authorized voice reference only`.
- Use the same image-order names throughout the prompt. Do not rename image 1 as one character in the setup and another character in the action.
- Keep one main scene reference per video prompt. If the story moves to a different location, split the shot.
- State whether each image is a start frame, end frame, character reference, scene reference, prop reference, expression reference, or storyboard reference.
- State each uploaded image's action phase: pre-action setup, middle action/reference, result/aftermath, character reference, scene reference, prop reference, expression reference, or motion reference.
- If a video reference is used, trim it to a short reference segment, preferably 15 seconds or less, and explicitly state what to reference: action, camera movement, rhythm, pose, or composition.

Motion reference and timed beat control:

- Use only legal or user-authorized motion references. Do not use copyrighted film, TV, game, influencer, celebrity, or music-video footage as a commercial reference unless the user owns or has cleared the rights.
- For professional action, fight, dance, magic/VFX, camera-movement, or impact-heavy shots, prefer a short motion reference when available. If none is available, create a motion plan with exact beat timing before writing the prompt.
- Separate control layers by purpose: character images lock identity and costume; scene images lock space and light; prop images lock scale and handling; start/end frames lock physical state; video references lock motion rhythm, camera rhythm, pose path, or impact timing only; audio references lock authorized voice only.
- Before prompt writing, decide the control priority for the selected model route. If the route cannot combine first/end frames with a video reference or cannot accept enough references, state which control layer is sacrificed and why; do not silently overload a route that cannot carry the shot.
- For finished sequences with several storyboard panels, generate each panel or clip segment separately, then stitch/edit the clips into the finished sequence. Do not compress the whole storyboard grid into one video generation call.
- A 5-second video prompt should usually contain 2-3 clear beats. An 8-10 second prompt can carry 4-6 beats. More beats need a longer duration, intermediate frames, or shot splitting.
- Every action beat must include wind-up or threat, acceleration or pressure increase, contact/near-miss/result, recovery/recoil/environment response, and the carry-forward state when relevant.
- Every fight/action beat must include action meaning and opponent response: protagonist tactic, enemy counter-pressure, viewer information delta, power-state change, start/end facing direction, and start/end spatial relation. A shot with only one isolated action and no reaction/counter-pressure is not generation-ready unless it is an intentional insert or aftermath.
- For VFX attacks, define the source, charge-up, release, travel path, impact point, environment response, sound cue, and aftermath. Do not ask the model to invent all action logic from a single phrase like "epic attack".
- For model routes with a minimum duration, such as local workflows that require at least 4 seconds, design one primary cinematic action and trim the best usable 1-3 seconds in editing if the episode needs a shorter insert.
- Before any expensive video generation, run a low-cost prompt preflight: check reference roles, frame phases, timing density, physical transition, character/scene consistency, style consistency, sound layer, and QC blockers. Failed preflight means revise before generation.
- Negative prompts must be precise and subordinate to the action. Do not write a negative list so broad that it removes the motion, impact, expression, or environmental response the shot needs.

Constrained-route execution prompt compression:

- Keep `director_layer` and `provider_execution_prompt` separate. The director layer may contain action meaning, audience comprehension, power-state logic, blocking, and continuity. The submitted provider prompt should contain only visible, shootable instructions.
- Compress the execution prompt into five parts: opening frame relation, one core action chain, one primary camera movement, result state, and no more than three critical guardrails.
- Convert abstract director language into visible evidence before submission. Examples: "viewer understands her tactic" becomes gaze, posture, low body path, exposed object position, and enemy gun angle; "the enemy loses tracking" becomes the gun barrel is close but cannot tilt low enough; "the prop means counterattack" becomes the hand grips the prop and its light/shape visibly changes the frame.
- For 5-6 second clips or otherwise low-control routes, avoid stacking three or more dense action phases, complex camera movement, sound design, prop logic, negative prompts, and audience-intent sentences in one prompt. When camera motion is the test target, put camera motion in the first sentence and reduce character-action detail.
- When output fails, change one variable per retry: composition first, then body action, then camera, then prop/result, then sound. Do not rewrite every layer at once.
- If the route supports references, assign roles explicitly: start frame locks composition, character reference locks identity/costume, scene reference locks space/light, prop reference locks scale/handling, video reference locks action or camera rhythm. If the route only supports text or one image, prefer a shorter execution prompt plus a stronger start frame over a long text prompt.

Style consistency under rejection:

- Lock the project style at the style-bible level before asset generation.
- If a still image, character reference, scene reference, prop reference, or storyboard frame is rejected, repair or regenerate it in the same approved project style unless the user explicitly approves a full project style migration.
- Do not convert only one blocked realistic/live-action/CG reference into 2.5D, anime, pencil, sketch, oil-painting, or another style while the rest of the episode stays in the original style.
- If the rejection is real-person, celebrity likeness, face imitation, or identity-risk related, do not bypass it through style conversion. Return to the character bible / character asset stage and redesign the character as an original fictional character in the approved project style.
- If a full style migration is approved, regenerate the affected character sheets, expression sheets, scene spatial packs, prop references, storyboard frames, and prompt pack before video generation continues.

Physical logic and bad-hand prevention:

- A still-frame prompt must describe one single physical moment, not a storyboard grid, not multiple beats, and not cause plus result in the same image.
- For hand/prop actions, split the action into stable states: approach, contact/grip, release/impact, aftermath, reaction. Generate start/end frames from the exact state needed for the video model.
- If hands are visible and story-critical, state left/right hand, contact point, object position, finger visibility, and what the hand is doing. If the exact hand pose is not story-critical, prefer safer camera design: sleeve/edge occlusion, over-shoulder framing, object close-up, reaction shot, silhouette, or crop the hand out.
- Never use an ending/result frame as the starting frame for the cause of that result. A broken glass image is an ending/target reference, not the first frame of the falling action.
- Never use a middle-action storyboard/reference frame as the starting frame if it skips the cause setup. A falling glass already in midair is not the start of a "glass slips from hand" shot.
- If a still image has bad hands, wrong grip, impossible contact, fused objects, floating objects, reversed left/right orientation, or body/prop penetration, do not pass it downstream. Retry, locally redraw, erase/repair, crop around the issue, or redesign the shot angle.
- For complex physical actions, prefer several short performable shots over one dense prompt: setup, motion, impact, result, reaction.
- When video continuity matters, extract a clean stable frame from the previous generated clip and use it as the next start frame, unless that frame already contains a physical or identity error.

## Video Prompt

Formula:

`who + where + doing what + how moving + expression change + camera movement + dialogue/open-mouth state + diegetic sound + Foley cues + continuity state`

Before writing video prompts for a project action, read the relevant compiled cache files and stage references, then update `00_knowledge_read_audit.md` with cache files opened, stage-cache artifacts reused, and rules applied. Use raw `rg` database searches only on cache miss, conflict, new material, user-requested relearning, or missing rule coverage. Do not write prompts from chat memory alone.

Before sending a video prompt to any model, run a prompt-source compliance check: re-open the relevant database and skill rules, compare the prompt against style, continuity, reference binding, sound taxonomy, start/end frame logic, model-route constraints, and QC blockers, then revise before generation if any item fails.

Rules:

- no pronoun-only references
- no hallucinated plot
- no subtitles, UI, watermarks, or BGM
- one shot equals one performable action or emotion turn
- repeated slashes, rapid punches, chained parries, or a flurry can be one continuous combo beat when it has one tactical objective, one spatial route, one camera design, and one result
- if the action is too dense, split the shot
- for multi-panel storyboard output, generate each panel/clip separately and stitch in editing; do not upload a full storyboard grid as the reference for one generated clip
- for constrained routes, do not paste the full director layer into the prompt; submit a compressed execution prompt with visible action, primary camera movement, result state, and minimal guardrails
- For first/end-frame prompts, describe camera movement and visible object/scene change. Use shorter durations only for small/natural transitions; use longer durations, intermediate frames, or shot splits when background, environment, camera angle, pose, or styling changes substantially.
- Do not force first/end-frame transitions across incompatible spaces or states, such as outdoor-to-indoor, day-to-night, or radically different character pose/clothing, unless an intermediate frame chain is provided.
- For multi-beat generation, write `shot size + camera movement + screen content` for each beat. Four distinct beats usually need longer duration, intermediate frames, or separate clips; a short constrained route is often too compressed.
- state whether uploaded images are starting frames, ending frames, character references, scene references, or prop references
- do not ask an ending-frame image to generate the earlier cause of that ending; create a correct starting frame instead
- when the target video model supports native audio, include a `sound layer` for every shot: character voice tone, spoken line timing, visible-source foreground Foley, object impact sounds, cloth movement, and deliberate silence. For any confirmed native dialogue/Foley route, keep this layer foreground-only.
- sound descriptions must be diegetic, visible/source-clear, and action-synced, e.g. glass shatters on marble floor at 0.2s, fountain pen rolls across polished table at 1.4s, chair scrapes softly, a forced door bursts open at 0.5s
- do not ask the video model for subtitles, readable UI text, watermark, generic BGM, room tone, ambience beds, or crowd chatter; if music or broad atmosphere is needed, keep it in post-production
- if model-generated voice/audio is unstable, mark the generated audio as failed or reference-only and replace with post-production expressive TTS/Foley
- If the final edit needs dialogue or dubbing, the video prompt must include the spoken line, speaker, language, emotion, and open-mouth/lip-sync state. Do not expect a closed-mouth shot to sync naturally in post.
- If the shot has visible physical action, include matching diegetic sound or Foley in the prompt and edit plan: cup hits floor, glass breaks, pen rolls on table, chair scrapes, footsteps, fabric friction, door click, forced door impact, breath.

### Sound Taxonomy

Use this distinction for every prompt and edit plan:

- Voice: named character, exact English line, emotion, pacing, and open-mouth/lip-sync state.
- Foreground Foley: sounds whose source is visible or story-focused on screen, such as glass breaking, cup impact, forced door impact, pen rolling, paper movement, chair scrape, footsteps, cloth movement, breath, a phone vibrating on the table, or a hand hitting the table.
- Deliberate silence: use when a reveal, humiliation beat, or power reversal needs tension.
- Post-production music: BGM, dramatic hits, risers, and music transitions are added in editing unless a tool route is explicitly testing native music.
- Forbidden background bed: banquet-hall chatter, crowd murmur, indistinct party conversation, restaurant ambience, room tone, wind/air hum, generic atmosphere, soundtrack beds, songs, lyrics, and generated BGM. These create abrupt audio cuts and make downstream editing worse.

If a scene visually contains many people, do not ask the video model for the crowd's background conversations. Write `No background ambience, no room tone, no crowd chatter, no indistinct party conversation, no music`.

### Confirmed Native Dialogue/Foley Route

When the selected video route is confirmed to support native dialogue/Foley or generated sound effects:

- Enable native audio/sound effects for every selected audio-capable video model unless the user explicitly disables it; do not write prompts such as "Audio is disabled" or "No Native Audio" for these routes.
- Each video prompt must ask the selected model to generate character dialogue from the approved script line, including speaker, exact spoken line, target language, emotion, timing, and open-mouth/lip-sync state.
- Each video prompt must ask the selected model to generate only foreground diegetic sound/Foley that matches visible or story-focused action and timing, such as glass shattering, a forced door opening, pen spinning or rolling, cup impact, chair scrape, paper movement, footsteps, cloth movement, and breath.
- Do not ask the selected model to generate background ambience, room tone, crowd chatter, indistinct party conversation, banquet-hall background conversations, music, BGM, songs, lyrics, soundtrack beds, subtitles, readable UI text, logos, or watermarks.
- If native voice or Foley is unusable, mark the audio as failed in the generation log and either regenerate the shot with corrected audio instructions or replace the failed layer in post-production. Do not keep duplicate generated voice plus post voice.
- No local or hosted workflow is the default native-audio route. If the selected route accepts only text or one uploaded image, use it only for explicitly approved text-only, single-reference, or emergency supplement shots.

## 6s Template

Output four parts:

1. shot information
2. still prompt
3. video prompt split into `0-2s`, `2-4s`, `4-6s`
4. ending state

Include an audio block in each video prompt:

- Voice: speaker, language, emotion, volume, pacing, and whether the mouth should open/sync
- Foley: visible object sounds with exact timing
- Foreground-only audio: visible/source-clear object sounds and body sounds; for any confirmed native dialogue/Foley route, write `No background ambience, no room tone, no crowd chatter, no indistinct party conversation, no music`
- Silence: use deliberate silence before reveals or after impacts
- Post fallback: list sounds that must be recreated if the generated audio fails

## 10s Template

Use for a compact conflict beat:

- `0-3s`: open
- `3-7s`: progress
- `7-10s`: result or reversal

Use 3-4 shots if necessary.

## 15s Group Template

Start with unified:

- style
- quality
- era
- scene
- light
- aspect ratio
- no text
- no subtitles
- no watermark

Then write each shot with:

- character state
- position
- action
- expression
- dialogue
- camera
- continuity
- sound layer

