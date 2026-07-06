# Workflow

Before each production stage in this workflow, read the relevant compiled knowledge cache and skill reference for that stage, then update `00_knowledge_read_audit.md`. Do not proceed from chat memory alone.

Every stage output must be constrained by local source-backed rules. Use `knowledge_compiled/` first. Run raw teaching-database lookup with `rg` only when the compiled cache misses, conflicts, new teaching material exists, the user requests relearning, or the needed rule is not covered. If both cache evidence and required raw-source evidence are missing, the stage output is invalid and must not be produced.

Every stage must pass a two-pass knowledge gate:

1. Stage-start read: before planning or writing the stage, read the relevant compiled cache and skill references; search raw teaching material only on cache miss/conflict/new material/user-requested relearning.
2. Pre-output compliance check: immediately before outputting the artifact or calling any image/video/audio/editing tool, compare the current artifact, prompt, or generation call against the loaded cache rules, stage-cache artifacts, asset gates, and QC blockers.

If the pre-output compliance check is missing or fails, revise the artifact/prompt first, repeat the check, and do not generate or deliver until it passes.

## 0. Delivery Gates

Every stage must expose three gates before its output is treated as usable:

- `knowledge_gate`: pass only when `00_knowledge_read_audit.md` records the stage-start cache read, opened local reference files, source-backed rules, stage-cache reuse decision if applicable, and `pre_output_compliance_check`. If cache miss or conflict required raw search, it must also record `rg` search terms and opened teaching files.
- `asset_gate`: pass for character stages only after every core character has four-view, expression, marker/detail, and close-up references; pass for scene stages only after every core scene has 720-degree/multi-angle references, camera positions, state variations, and prop close-ups.
- `qc_gate`: pass only after the current artifact or generated output has been inspected against `references/qc-gates.md`.

No audit entry means no artifact. No asset gate means no serious video generation. No QC pass means no delivery.

If any gate is missing, failed, or unverified, set `allowed_output` to `blocked_report_only`. The only valid output is a blocker report naming the missing reads, missing assets, failed QC rule, and retry route. Do not present failed images, failed clips, or uninspected clips as results.

When a project package exists, run the local gate validator before user-facing delivery:

Run the local delivery validator configured for the current host when one exists. If no executable validator is configured, record `executable_gate: N/A` and rely on the documented gate evidence.

Validator failure means the workflow must stay in the current or nearest upstream stage until the missing reads, assets, or QC fixes are completed.

## 1. Idea Intake

Capture:

- original idea
- target audience
- target platform
- duration
- visual style
- commercial target
- forbidden zones

Gate: the idea must have conflict, protagonist goal, and reversal potential.

## 2. Audience Route

Female-frequency:

- emotional value
- relationship pull
- male-lead aesthetic
- eye contact, hesitation, hand contact, breath, fabric, wind, light, slow motion

Male-frequency:

- çˆ½ç‚¹
- æ‰“è„¸
- é€†è¢­
- power reversal
- visible result
- faster rhythm and harder impact

Common:

- first 3 seconds need a hook
- every episode needs conflict progression
- ending needs reversal or next-episode hook

## 3. Story Bible

Must include:

- world and era
- protagonist goal
- core conflict
- character relationships
- episode outline
- hooks and reversals
- series engine handoff: repeatable viewing promise, long-arc desire, per-episode payoff mechanism, pressure escalation route, secret/evidence/payoff ledger, and episode-cluster reversal plan

If adapting text, do not add plot or change causality. Convert inner emotion into visible behavior.

## 3B. Series Engine

Create `01C_series_engine.md` before serious episode scripting when the project is a repeatable series, not a one-off clip.

Required fields:

- `viewing_promise`: why the audience returns episode after episode.
- `long_arc_desire`: what the protagonist wants across the season or test arc, separate from the single-episode goal.
- `episode_payoff_mechanism`: the repeatable emotional value, çˆ½ç‚¹, fear, mystery, romance pull, humiliation reversal, or proof reveal each episode must pay off.
- `pressure_escalation_ladder`: how antagonist pressure, social pressure, danger, stakes, or relationship cost rises over episodes.
- `secret_evidence_payoff_ledger`: what information, object, identity, debt, betrayal, clue, or promise is planted, who knows it, who misreads it, and when it pays off.
- `cluster_reversal_plan`: 3-episode, 5-episode, and 10-episode reversal or escalation targets when the series length requires them.
- `audience_knowledge_state`: what the audience knows that characters do not, and what characters know that the audience does not.

Rules:

- Do not build every episode from a fresh random twist. A series needs a repeatable engine that can generate new pressure and payoff without breaking causality.
- Do not use a single cliffhanger as the whole engine. The engine must define desire, pressure, payoff, and information control.
- If the series engine is missing, mark professional series packaging as `series_engine_not_ready`.

## 3A. Professional Production Layer

Every serious episode must create these professional planning artifacts before storyboard or prompt generation:

- `series_engine`: viewing promise, long-arc desire, per-episode payoff mechanism, pressure escalation ladder, secret/evidence/payoff ledger, cluster reversal plan, and audience knowledge state.
- `director_treatment`: episode premise, visual keywords, emotional curve, camera grammar, rhythm style, color/light route, sound route, and what this episode should feel like as a finished watch.
- `reference_board`: 2-3 visual reference directions with what to borrow and what not to copy: camera grammar, lighting, color, production design, pacing, performance tone, or VFX scale. Do not use copyrighted characters, faces, music, or exact protected frames as commercial content.
- `theme_and_mise_en_scene`: episode theme, visual motifs, power-space grammar, recurring composition rules, psychology-to-space/light changes, motif reversal, and cheap-emotion prohibitions.
- `coverage_plan`: master shots, clean singles, over-shoulders, inserts, reactions, proof/object shots, transitional cutaways, atmosphere shots, and safety shots needed for editing.
- `blocking_plan`: character movement paths, power positions, who approaches/retreats, who blocks whom, eye-line relations, distance changes, and prop handoff paths.
- `performance_direction`: subtext, internal want, line intention, pause, breath, gaze shift, micro-expression, restraint/explosion point, reaction timing, scene objective, obstacle, tactic, beat changes, playable action verbs, emotional temperature, and reaction priority.
- `lens_camera_language`: camera height, lens feeling, distance, compression/space, handheld/stabilized/tracking/drone feeling, depth of field, and why the lens choice supports the beat.
- `light_color_script`: episode color arc, scene color palette, light source logic, contrast curve, warm/cold shift, shadow plan, highlight/rim strategy, and reveal darkness.
- `production_design_texture`: costume, makeup, hair, material, aging/wear, social class, prop symbolism, object texture, space dressing, and status symbols.
- `prop_and_evidence_ledger`: repeated props, proof objects, identity markers, contracts, phones, clues, weapons if allowed, ownership, first appearance, viewer/character knowledge, physical state changes, required close-ups, post text plan, and reversal function.
- `editing_rhythm_map`: hook cut rhythm, hold points, reaction duration, proof insert timing, speed ramps if any, silence beats, transitions, and ending hook cut.
- `sound_director_layer`: voice performance, Foley priority, silence, music entry/exit, riser/hit points, sound bridges, room tone exclusions, and foreground-only native-audio rules.
- `cinematography_bible`: aspect ratio, lens/focal rules, camera support, camera height, depth of field, exposure/contrast, movement restrictions, shot-family rules, and visual continuity of the camera system.
- `previs_animatic_plan`: rough shot timing, dialogue-to-picture fit, action continuity, edit rhythm, music/Foley cue placement, missing inserts, risk shots, and split/regenerate decisions before prompt writing.
- `audience_comprehension_map`: every-3-second viewer knowledge, clue/emotion delta per shot, intended viewer question, misdirection clarity, silent-watch readability, and reversal setup/payoff check.

If these artifacts are absent, mark the project as `not_professional_ready` and do not produce generation-ready prompts.

## 3C. Theme And Mise-en-scene

Create `01D_theme_and_mise_en_scene.md` after director treatment and before storyboard for professional-level output.

Required fields:

- `theme_statement`: the episode's dramatic idea in one sentence.
- `visual_motifs`: recurring doors, glass, mirrors, contracts, rings, rain, shadows, screens, weapons, fabric, flowers, or other objects that carry theme.
- `power_space_grammar`: who is high/low, centered/edge, blocked/open, near/far, reflected/direct, or inside/outside at each power state.
- `psychology_to_space_light`: how inner change becomes distance, posture, blocking, shadow, color temperature, reflection, enclosure, or exposure.
- `composition_motif_and_reversal`: repeated framing pattern and how it flips at the reversal or ending hook.
- `forbidden_shortcuts`: cheap emotional devices the episode must not rely on, such as crying close-ups without action, yelling instead of tactic, unmotivated slow motion, or explanatory dialogue replacing behavior.

Rules:

- Do not treat theme as a slogan. It must change blocking, light, props, and composition.
- Do not use the same neutral mise-en-scene for romance, humiliation, suspense, grief, revenge, and power entrance.
- If theme/mise-en-scene is missing, professional storyboard and prompt writing must be marked `theme_mise_en_scene_not_ready`.

## 4. Script Package

Every episode needs:

- 0-3s hook
- conflict progression
- visible action
- dialogue that carries relation or information
- ending hook

Do not replace key conflict with narration.

## 5. Character Bible

Each core character needs:

- age
- face and features
- hair
- body proportion
- fixed outfit
- marker
- default expression
- relationship role
- audience aesthetic check

Character asset pack is required before serious video generation:

- four-view sheet: front, left, right, back, same clothes, same hair, same body proportion
- expression sheet: neutral, restrained, angry, contempt, shocked, cold smile, hesitant/panicked as needed
- marker detail sheet: watch, cufflinks, earrings, brooch, pen, folder, or other identity anchors
- close-up reference: clear face and upper body for reaction shots

Use original characters only for commercial work.

## 6. Scene Bible

Scene formula:

`style + scene subject + time/weather + emotional atmosphere + details + camera/light`

The scene must be recognizable, spatially usable, and ready for reverse angles or state variations.

Scene spatial asset pack is required before serious camera movement:

- 720-degree/multi-angle references: front, back, left, right, front-left, front-right, back-left, back-right
- key camera positions: entrance, screen, table, protagonist position, antagonist position, guest area
- state variations: before conflict, reversal moment, aftermath
- prop close-ups: papers, pen, phone, glass, screen blank, bags, weapons only if allowed

A single mood image cannot replace a spatial pack when reverse shots or moving cameras matter.

## 6A. Prop And Evidence Ledger

Create `03C_prop_and_evidence_ledger.md` before storyboard when the story uses repeated props, proof objects, clues, contracts, phones, messages, identity markers, weapons if allowed, or any object that triggers a reversal.

Required fields:

- `prop_or_evidence`: object name and visual identity.
- `story_function`: proof, identity, threat, memory, wealth/status, relationship token, deception, clue, weapon if allowed, or reversal trigger.
- `owner_and_handler`: who owns it, who holds it, who sees it, who hides it, and who misreads it.
- `first_appearance_and_payoff`: first shot where it must be visible, later shot where it changes meaning, and payoff shot.
- `physical_state_changes`: clean, signed, broken, hidden, revealed, stolen, dropped, opened, blank-for-post-text, or destroyed.
- `required_closeups`: exact close-up or insert shots needed so the audience believes the evidence.
- `text_or_screen_plan`: whether readable text is forbidden in generation and must be added in post.
- `continuity_risks`: scale, grip, left/right hand, screen UI, readable text, material drift, or missing state change.

Rules:

- Do not let a reversal depend on a prop that the audience never clearly saw.
- Do not ask image/video models to generate readable legal documents, phone UI, or evidence text when post-production text is safer.
- Repeated props need independent prop references plus character-bound scale/use-state references when handling matters.

## 7. Storyboard

Fields:

`shot id | shot type | duration | dramatic function | coverage role | visual intent | scale class | viewer attention | shot size | composition hierarchy | lens/camera language | camera motivation/movement | transition design | lighting design | color note | depth design | reveal path | scene id | character | screen position | body state | blocking movement | prop state | action phase | action | expression/performance note | environment/VFX response | dialogue/subtext | sound | frame phase plan | still prompt notes | video prompt notes | previous state | start/end frame rule | continuity`

Rules:

- one shot equals one performable segment
- split dialogue, action, reaction, prop changes, and emotional turns
- add establishing shots for time/place changes
- avoid static reverse-shot overuse
- continuity fields are baseline control, not cinematic expression; do not treat left/right positions and hand poses as a complete visual design
- every shot in every genre must include a professional direction pass: dramatic function, viewer attention, camera motivation, movement design, transition design, lighting design, depth design, and rhythm
- every shot must name its coverage role: master, clean single, over-shoulder, reaction, insert, proof/object, transition, atmosphere, VFX plate, or safety shot
- every performance-heavy shot must include subtext, pause/breath, gaze shift, micro-expression, and reaction timing
- every scene must have enough coverage to edit: at least one spatial/master or establishing reference, key close/reaction shots, needed inserts, and a transition or atmosphere option when the scene changes
- do not write generic camera filler such as "medium shot, slow push-in, cinematic lighting" unless it has a clear dramatic function and changes what the viewer feels or learns
- camera movement must be motivated by reveal, concealment, pressure, intimacy, status shift, suspicion, comedy timing, impact, or emotional turn
- transitions must be designed, not defaulted: action cut, eye-line cut, reaction cut, object wipe, foreground occlusion, match cut, sound bridge, J-cut, L-cut, smash cut, or deliberate hard cut
- lighting must support the beat: source, direction, contrast, color temperature, shadow, rim/back light, practical light, silhouette, reflection, or darkness reveal
- every spectacle, fantasy, Eastern-aesthetic, large-scene, or VFX battle shot must include `visual intent`, `scale class`, `composition hierarchy`, `camera motivation`, `reveal path`, and `environment/VFX response`
- if a requested epic shot can be reduced to "two characters stand facing each other and powers collide", split or redesign it before prompt writing
- every combat shot, regardless of genre or scale, must include combat dynamics: pressure, tension, speed cue, power transfer, impact result, resistance, and aftermath
- combat storyboard notes must show wind-up/threat, acceleration, contact or near-miss, recoil/environment response, and reaction or next danger
- do not write "fight fiercely", "attack each other", "powers collide", or "moves quickly" as a complete combat design; specify force direction, speed evidence, contact point, target resistance, and result
- A continuous combo such as repeated slashes, rapid punches, chained parries, or a flurry of blows can be one performable combat beat when it has one tactical objective, one spatial route, one camera design, and one result. Do not split a readable combo merely because it contains several strikes. Split only when the combo changes target, location, tactic, power relation, prop state, or required camera coverage.
- before generating any starting frame, storyboard/reference frame, or ending frame, create a frame phase plan that maps each image to a distinct causal phase of the shot
- carry forward the previous shot's physical state when it matters: who is standing, seated, fallen, approaching, holding a prop, left/right/on screen, or looking at whom
- do not paste next-shot guidance into the current model prompt; continuity notes are for the creator unless they describe the current shot's actual starting state
- every physical action must have a plausible start state and end state before image or video generation
- every sound field must separate character dialogue, visible-source foreground Foley, deliberate silence, post-production music, and forbidden background bed
- background bed must stay out of generated clips: no banquet-hall chatter, no crowd murmur, no indistinct party conversation, no room tone, no generic ambience, no music

Frame phase rules:

- Starting frame = pre-action setup, before the cause begins or at the exact first controllable state. For a glass slipping shot, the starting frame is the glass still in the character's hand, fingers losing grip, not already in midair.
- Storyboard/reference frame = representative middle action or composition guide. For a glass slipping shot, it can show the glass halfway through the fall, motion direction clear, hand above, floor below.
- Ending frame = result/aftermath state after the action. For a glass slipping shot, it is broken glass and spilled liquid on the floor/table, with character reaction or aftermath if needed.
- Do not use a storyboard/reference image or ending/result image as the starting frame for a cause-and-effect action.
- If the action has more than three important physical phases, create intermediate frames or split the shot before video generation.
- The frame phase plan must list: `starting_frame_phase`, `storyboard_reference_phase`, `ending_frame_phase`, `physical_transition`, `missing_intermediate_frames`, and `invalid_frame_reuse_risk`.

Shot type route:

- Single shot: use for missing inserts, object close-ups, reaction shots, facial expressions, hand slams, one look, one spoken line, or one independent action.
- Multi-shot: use only when the material shares one scene id, the same or few characters, and continuous small actions. Keep one generated clip focused on one shot or one continuous combo beat; generate multiple clips for multiple storyboard panels, then edit/stitch them into the finished sequence.
- Storyboard sheet default: when generating more than one storyboard panel for a sequence, default to one full storyboard sheet/grid first so style, lighting, character placement, and shot order can be reviewed together. The sheet must include reading order, story beat, character relationship, target emotion, and panel boundaries when the image model can support it.
- Single-panel exception: generate a standalone storyboard frame instead of a full sheet only when the shot is a one-off, when the image model repeatedly fails the sheet layout, when a panel needs unusually high detail, or when a confirmed video route needs a dedicated first frame rather than a storyboard reference.
- Video-reference crop rule: a full storyboard sheet/grid is for planning, review, and selecting panels only. Do not upload the whole multi-panel grid as a video reference for one generation. For video generation, crop the intended panel or create a dedicated single-panel/frame reference for each generated clip.
- Arrow-guide rule: motion/camera/prop arrow guides must be made from a duplicate of the cropped single panel or dedicated frame. Do not draw arrows on the full storyboard sheet for video generation. If arrow direction cannot be trusted or may confuse the model, omit the arrow guide and use text/key-pose control instead.
- Split instead of merging when the scene changes, more than three characters must be tracked, a prop changes physical state, a body position changes, or dialogue and action compete for timing.

## 7A. Cinematography Bible

Create `04G_cinematography_bible.md` for professional-level output before final prompt writing. This file upgrades per-shot lens notes into a consistent camera system for the whole episode.

Required fields:

- `aspect_ratio_and_framing`: target aspect ratio, safe frame, close-up rules, headroom, negative space, and mobile-readable composition.
- `lens_package`: wide/normal/telephoto/macro/aerial lens families, when each may be used, and what emotional or spatial effect each creates.
- `focal_length_rules`: which character, power state, scene type, or story beat gets wide, normal, compressed/telephoto, macro/detail, or aerial feeling.
- `camera_support_rules`: locked-off, handheld, stabilized, tracking, crane/drone-like, orbit, push/pull, whip-pan, and when each is forbidden.
- `camera_height_power_rules`: eye level, low angle, high angle, overhead, ground-level, shoulder-level, and how height expresses status, intimacy, pressure, vulnerability, or scale.
- `depth_of_field_strategy`: deep focus, shallow focus, rack focus, foreground occlusion, reflection, and what each reveals or hides.
- `exposure_contrast_texture`: high/low key, silhouette, rim/back light, flare, reflection, shadow density, highlight control, and practical-light logic.
- `movement_restrictions`: camera moves that must not be overused, genre-specific movement limits, and when a locked frame is stronger than a moving frame.
- `shot_family_continuity`: recurring camera grammar for protagonist, antagonist, romance, humiliation, power entrance, action, proof inserts, and cliffhangers.

Rules:

- Do not let every shot invent a new lens logic. A professional episode needs a recognizable camera system.
- Camera choices must be tied to story function, power relation, emotion, scale, or information reveal.
- If a prompt uses "cinematic lens", "slow push-in", "shallow depth of field", or "handheld" without inheriting this bible, it is not professional-ready.

## 7B. Anime Battle Direction Layer

Required when the user asks for top-tier anime battle, donghua/anime-style combat, xianxia anime action, stylized 2D/2.5D/3D anime fighting, or any fight where the target quality depends on animation timing, key poses, combo design, and FX language.

Create `04E_anime_battle_direction.md` before prompt writing. This layer does not replace storyboard or frame phase planning; it translates the fight into animation-industrial control.

Required fields:

- `animation_timing_chart`: anticipation, hold, acceleration, impact frame, recoil, follow-through, recovery, and any intentional smear/impact-frame hold.
- `key_pose_sheet`: start pose, wind-up pose, burst pose, contact pose, hit reaction pose, aftermath pose, readable silhouette, line of action, and limb/weapon direction.
- `character_combat_style`: each fighter's combat personality, movement rhythm, preferred distance, attack route, defense habit, signature weapon/energy shape, and weakness.
- `combo_chain`: probe, evade, counter, guard break, chase, reversal, finisher, interruption, or cliffhanger. Do not make every shot a disconnected single attack.
- `anime_fx_bible`: shape language, color, edge style, motion trail, speed lines, aura, sparks, smoke, dust, debris, shockwave, magic circle, lightning/fire/water/weapon energy behavior, and how FX affects clothes, hair, props, ground, sky, or clouds.
- `anime_editing_grammar`: stillness-to-burst, cut-in, reaction cut, impact frame, speed-line wipe, black-frame hit, match-on-action, foreground wipe, fast insert, silence hold, and rhythmic hold/release.
- `battle_space_map`: positions, distance, height, ground/air state, axis, camera side, attack direction, retreat path, obstacles, destructible terrain, and terrain changes after each exchange.
- `action_meaning_map`: every character action must state tactical purpose, character intention, opponent counter-pressure, what the viewer learns or feels, and how the power relation changes.
- `spatial_continuity_map`: fixed battlefield coordinates, each character's start/end position, facing direction, screen direction, body state, prop state, camera side, axis rule, and carry-forward state from previous shot to next shot.
- `layered_generation_plan`: layout layer, key-pose layer, action-timing layer, FX layer, camera layer, impact layer, sound layer, and continuity layer.

Rules:

- A top-tier anime fight prompt is invalid if it only says characters attack, dodge, clash, or release energy without key poses, animation timing, combo continuity, FX language, and battle-space continuity.
- A fight prompt is invalid if it only describes motion without meaning. The viewer must understand why the character moves, what the opponent does in response, what information changes, and how the power relation shifts.
- If a shot starts from a position, posture, facing direction, or prop state that cannot inherit from the previous shot, return to battle-space planning or add a transition/reset shot before prompt writing.
- Every major attack must have at least one readable silhouette or contact pose that can be judged as a still frame.
- FX must have a consistent design rule; do not vary sword energy, magic circles, smoke, sparks, and aura randomly from shot to shot.
- Camera and editing must serve the animation timing. Use holds, sudden acceleration, impact frames, reaction cuts, and aftermath silence intentionally.
- If the selected video model cannot follow dense anime battle direction in one clip, split into layout/key-pose stills, short action clips, impact inserts, reaction shots, and FX plates.

Fight Final Mode:

- Use `fight_final` for final battle shots, key impact shots, xianxia/donghua hero moments, live-action-style melee, or any shot where the user expects premium fight quality rather than a rough idea.
- Build the shot in three layers before writing the provider prompt: `director_layer` for story meaning and power relation, `action_graph_layer` for spatial/contact/VFX/prop logic, and `execution_layer` for the compressed provider prompt plus API params.
- Required combat compiler fields: `style_route`, `fight_director`, `combat_beat`, `impact_system`, `vfx_power`, `camera_coverage`, `provider_route_strategy`, `provider_execution_prompt`, `negative_constraints`, `asset_bindings`, `qc_expectations`, `combat_qc_score`, and `qc_evidence`.
- Split the shot if it contains more than one tactical objective, more than two visible contact events, more than one major camera behavior, or more than one major VFX state shift.
- A fight prompt is not final-ready until the first visible contact point, opponent reaction, force direction, prop state change, VFX attachment, end state, and next-shot carry-forward are all readable as visible evidence.

## 7B-2. 3D Donghua Action Layout Layer

Required when the project targets top-tier 3D å›½æ¼«, 3D anime-style battle, cinematic xianxia 3D combat, stylized CG martial action, or any fight whose quality depends on 3D layout, animation mechanics, FX-light integration, and action readability.

Create `04F_3d_donghua_action_layout.md` after `04E_anime_battle_direction.md` and before prompt writing. This layer does not replace anime battle direction; it converts the fight into 3D animation production control.

Required fields:

- `layout_blocking_map`: terrain coordinates, character start/end positions, height levels, camera side, screen direction, axis rule, reset points, and safe spatial anchors.
- `camera_character_trajectory`: camera path, character path, parallax layers, foreground/midground/background crossing, occlusion/reveal points, speed changes, and when the camera must stop so the action reads.
- `action_meaning_and_viewer_delta`: each movement's tactic, emotional/strategic meaning, opponent response, viewer knowledge change, and power-state change.
- `animation_mechanics`: center of gravity, root motion, foot planting, hip/shoulder rotation, weapon arc, landing buffer, recoil, follow-through, balance recovery, and secondary motion for hair, cloth, sleeves, ribbons, armor, or accessories.
- `contact_and_ik_notes`: hand/weapon grip, foot-ground contact, collision point, shield/weapon contact, body penetration risks, prop scale, left/right limb control, and when to crop/occlude to avoid bad contact.
- `fx_light_compositing_binding`: how energy, sparks, smoke, dust, shockwave, aura, magic circles, debris, and weapon trails cast light, create shadows, reflect on skin/costume/ground, obscure or reveal silhouettes, and layer in foreground/background.
- `battle_asset_state_pack`: combat outfit state, weapon states, energy-form turnarounds, damage/dirty states, facial strain, scene destruction states, debris assets, and before/mid/after environment variants.
- `action_readability_qc`: readable silhouette, clear attack line, visible anticipation, impact frame/hitstop, contact/result clarity, no motion blur over key pose, no camera shake hiding the strike, and clear winner/loser state after the exchange.

Rules:

- A top-tier 3D donghua fight is invalid if it only has pretty key poses and FX without layout, root motion, contact, camera trajectory, and compositing logic.
- Do not let camera movement compete with the attack line. If the viewer cannot read who moved where, split the shot or lock the camera for the impact.
- Every major strike must have a visible body-mechanics source, contact/near-miss relation, target resistance, impact frame or hitstop, and changed physical state.
- FX must interact with the 3D scene: light spill, shadow, reflections, cloth/hair response, dust/debris, atmospheric occlusion, and aftermath state.
- If a video model cannot carry 3D layout and animation mechanics in one clip, split into layout stills, key-pose sheets, short action clips, FX plates, impact inserts, and aftermath/reaction shots.

## 7C. Fight Director Layer

Use this layer for every combat request before storyboard-to-video prompt writing. It is mandatory for fights, duels, weapon clashes, hand-to-hand exchanges, magic collisions, avatar/dharma-body, suppression, domain expansion, burst attacks, reversals, dominance, 3D guoman battles, 2D high-dynamic combat, and live-action blockbuster-style fight coverage.

First build a Fight Map:

- `battlefield_layout`: terrain, obstacles, height, foreground/midground/background, safe spatial anchors
- `combatant_positions`: each character's start/end side, distance, height, facing, screen direction, body state, weapon/prop state
- `power_scale`: human-readable action, enhanced physicality, weapon/skill reveal, VFX collision, avatar/domain, aftermath scale
- `rhythm_map`: stillness, acceleration, contact, hitstop, recoil, reaction, aftermath hold, cut point
- `escalation_map`: how each shot raises or lowers pressure without jumping straight to full-screen effects
- `coverage_plan`: layout, approach, exchange, contact insert, reaction, environment impact, power reveal, aftermath, transition hook

Then build a Combat Beat for each shot:

- `tactic`: what the active character tries to accomplish
- `counter_pressure`: what the opponent does to resist or make the move difficult
- `contact_or_collision`: the first readable contact point, clash, near-miss, or force boundary
- `impact_feedback`: recoil, sparks, dust, air ripple, floor marks, water, cloth, prop vibration, or light spill
- `reaction`: body, weapon, environment, and power-state response after contact
- `result_state`: who has advantage and how the next shot inherits position, body state, facing, prop state, and VFX state

Rules:

- Do not generate a normal video prompt directly from a combat idea. First produce a structured combat compiler artifact.
- A large set piece must be split across shots; one prompt cannot generate a complete battle.
- Do not provide real-world fighting instruction, gore, or real injury detail. Keep action as fictional screen choreography and PG-13 impact language.
- Do not use specific IP names, character names, or direct style imitation as the route. Use original type language such as `3d_guoman_cinematic`, `2d_ink_anime_high_impact`, or `live_action_blockbuster_fight`.

## 7D. Combat Prompt Compiler Layer

For each combat shot, create `combat_prompt_compiler_output.json` or an equivalent object validated against `schemas/combat_prompt_compiler_output.schema.json`.

Required sections:

- `fight_director`: fight intent, combatants, tactical objective, opponent counter-pressure, spatial map, action chain, result state, risk level, readability plan
- `combat_beat`: beat type, screen action, tactical meaning, anticipation, contact/collision, impact feedback, reaction, aftermath, camera logic, VFX logic, continuity out
- `impact_system`: impact level, pre-impact, contact frame, hitstop, recoil, environment feedback, sound hint, aftermath pose
- `vfx_power`: VFX type, source, shape, behavior, color, body/environment interaction, visibility rule, start/peak/end states
- `camera_coverage`: shot type, distance, lens feel, motion, screen direction, subject priority, cut point, continuity in/out
- `provider_route_strategy`: selected provider route label, route class, duration, complexity, references, first/end frame plan, compression rule, unsupported controls, fallback route
- `prompt_human_readable_zh`, `prompt_canonical_en`, `provider_execution_prompt`, `negative_constraints`, `asset_bindings`, `qc_expectations`, `combat_qc_score`

Provider route strategy:

- `high_control_final`: use when the user's confirmed route supports the controls needed for complex contact, avatar, domain, suppression, magic collision, layered VFX, final shots, or multi-reference continuity. Prefer first frame, key pose, end frame, character/scene/prop references, and VFX style reference when the selected provider supports them.
- `fast_draft`: use for short draft tests with one action chain, one contact, one result. Do not use rigid timecodes by default; use soft beat order. If the route fails from overload, create key-pose stills and retry image-to-video, escalate to a higher-control route, or split the shot.
- `manual_upload` or `other_confirmed_route`: use when the user provides a web UI, local tool, hosted gateway, or custom provider route. Record unsupported controls and do not pretend missing features exist.
- `package_only_dry_run`: use when generation tools are unavailable. Produce the package or prompt pack, mark generation blocked, and do not claim media has been generated.

Combat QC:

- Score `action_readability`, `tactical_clarity`, `contact_believability`, `impact_feedback`, `spatial_continuity`, `vfx_readability`, `style_consistency`, and `cutability` from 0-5.
- Any score below 4 blocks render and requires rewrite.

## 7E. Previs And Animatic Plan

Create `04H_previs_animatic_plan.md` before prompt writing for professional-level output. It is the rough-cut thinking layer: the project should prove the scene can cut, breathe, sync, and land before spending generation credits.

Required fields:

- `rough_timeline`: shot order, estimated duration, hold points, speed changes, and total scene/episode duration.
- `dialogue_picture_fit`: which line is on-screen, off-screen, over reaction, over insert, or split across shots; note lines that are too long for the usable picture.
- `action_continuity_check`: whether motion, screen direction, prop state, body position, eyeline, and impact aftermath connect across shots.
- `edit_rhythm_map`: where the scene uses stillness, fast cuts, reaction holds, inserts, proof shots, silence, music hits, or hard cuts.
- `music_foley_cue_map`: where dialogue, foreground Foley, silence, risers, hits, and music phrase points land; avoid abrupt scene-boundary sound cuts.
- `missing_insert_list`: objects, hands, reactions, atmosphere, proof shots, transition shots, safety shots, and cutaways needed to make the edit work.
- `generation_risk_map`: high-risk shots, likely model failures, split/regenerate strategy, backup insert plan, and max retry budget.
- `animatic_decision`: pass, revise storyboard, split shot, add insert, shorten dialogue, change camera, regenerate asset, or block.

Rules:

- Do not generate final prompt packs if the rough timing does not fit the script.
- If dialogue continues after the picture changes without a planned reaction/insert/continuation shot, revise before generation.
- If action continuity cannot be followed in the rough timeline, return to storyboard, frame phase, or battle-space planning.
- Missing inserts are production blockers, not optional polish, when the edit needs them to hide model defects, carry dialogue, or preserve continuity.

## 7F. Audience Comprehension Map

Create `04I_audience_comprehension_map.md` before prompt writing for professional-level output. This file checks whether the viewer understands the right thing at the right time, especially on a phone and under silent/autoplay conditions.

Required fields:

- `three_second_knowledge_beats`: what the viewer must know or feel at 0-3s, 3-6s, 6-9s, and each following beat.
- `shot_information_delta`: what each shot adds: new fact, proof, emotional shift, relationship change, danger, misdirection, or payoff.
- `viewer_question_track`: what question the viewer should be asking at each moment.
- `clue_vs_emotion_split`: which elements prove facts and which elements create feeling.
- `misdirection_clarity`: where the story misleads intentionally without causing basic confusion.
- `silent_watch_readability`: whether the scene still reads from action, blocking, expression, props, and captions/post text when sound is off.
- `reversal_setup_payoff_check`: whether the ending reversal has visible setup that can be remembered.

Rules:

- Do not rely on the audience remembering hidden information that was never clearly shown.
- Do not confuse mystery with confusion. The viewer may wonder what happens next, but must understand what is happening now.
- If silent-watch readability fails for a platform-first short drama, revise storyboard, inserts, captions/post text plan, or prop evidence shots before prompt writing.

## 8. Prompt Pack

Generate still prompts before video prompts. The still image sets the quality ceiling and reference consistency.

Before writing still prompts for any shot, write a frame phase plan. Then write separate prompts for:

- starting frame: pre-action setup
- storyboard/reference frame: middle action or visual composition reference
- ending frame: result/aftermath

These prompts must not be interchangeable. Each one must state its image purpose and action phase before the visual description.

Still-image blocks during photos, storyboard frames, character assets, scene assets, or prop assets are retryable. Retry with a compliant prompt that preserves the approved story beat, character DNA, scene anchors, and asset purpose. Log the original problem, changed prompt/visual handling, retry count, output file, and QC result, then explain the issue and change after the batch or shot is completed.

Model rejection is a QC event, not permission to drift style. If a reference is rejected, repair it in the approved project style. Do not switch only the rejected image or shot to 2.5D, anime, sketch, pencil, oil-painting, or another style while the rest of the project stays realistic/live-action/CG. If the user approves a new style for cost, safety, or model acceptance, migrate the whole affected package: character sheets, expression sheets, scene packs, prop references, storyboard frames, and prompts.

Every generated image must be labeled before use:

- starting frame
- ending frame
- character reference
- expression reference
- scene spatial reference
- prop reference
- storyboard reference

Do not use an ending frame as a starting frame for a process action. If only an ending frame exists, the video prompt may only ask for subtle settling or atmosphere, not the full cause-and-effect action.

Use 6s, 10s, or 15s group templates based on action density and tool capability.

Prompt packs must include an explicit foreground-only audio block when the selected video route supports native dialogue/Foley or generated sound effects: approved character dialogue and visible/source-clear Foley are allowed; banquet-hall background conversations, crowd murmur, room tone, generic ambience, and music are forbidden and should be written as `none`.

For top-tier anime battle shots, prompt packs must inherit `04E_anime_battle_direction.md` and include:

- animation timing chart per shot
- key pose / silhouette notes for start, burst, contact, hit reaction, and aftermath
- combo-chain position: probe, evade, counter, guard break, chase, reversal, finisher, interruption, or cliffhanger
- anime FX bible binding: shape, color, trail, smoke/dust/debris behavior, aura, sparks, shockwave, magic circle, and environment response
- battle-space map state before and after the shot
- layered generation plan: layout, key pose, action timing, FX, camera, impact, sound, continuity

For top-tier 3D donghua battle shots, prompt packs must also inherit `04F_3d_donghua_action_layout.md` and include:

- layout blocking map and safe spatial anchors
- camera/character trajectory with parallax, occlusion/reveal, and readability stop points
- animation mechanics: root motion, center of gravity, foot planting, hip/shoulder rotation, recoil, follow-through, and secondary motion
- contact/IK notes for grips, collisions, foot contact, left/right limbs, and penetration risks
- FX-light-compositing binding: light spill, shadows, reflections, silhouette occlusion/reveal, debris, smoke, dust, and aftermath state
- battle asset state pack: costume/weapon/energy/damage/scene destruction before, during, and after
- action readability QC: silhouette, attack line, anticipation, impact frame/hitstop, contact clarity, motion-blur limit, camera-shake limit, and winner/loser state

Provider route capability additions:

- Before choosing any generation route, verify the selected provider's current capability, cost, commercial terms, reference limits, duration limits, native-audio support, moderation limits, and output ownership.
- If the selected route is Seedance/Jimeng-style, read `knowledge_compiled/seedance_rules.md`. If the host provides newer provider-specific source summaries, read the relevant sections and record them in the knowledge audit.
- Do not treat plain text-to-video or one random image-to-video pass as the serious-series route when character and scene consistency matter.
- Prefer multi-reference, subject reference, all-purpose reference, or smart multi-frame when the tool/account supports it.
- Label every uploaded asset by role before writing the action: character reference, clothing reference, shoe/accessory reference, scene reference, prop reference, start frame, end frame, storyboard/action reference, authorized voice reference, or video-motion reference.
- If using a video reference, trim it to a short reference segment, preferably 15 seconds or less, and state whether the model should reference action, camera, rhythm, or pose only.
- If using first/end frames, make sure the two frames form a plausible physical transition. Use 5 seconds for small/natural changes, 10 seconds or intermediate frames for larger changes.
- Four short storyboard beats usually need about 10 seconds; 5 seconds is often too compressed for four distinct beats.
- For short/fast/low-control routes, separate the internal director layer from the submitted execution prompt. The internal layer may include audience comprehension, action meaning, power-state logic, blocking, and continuity. The submitted prompt must be compressed into visible, shootable instructions: opening frame relation, one core action chain, one primary camera movement, result state, and no more than three critical guardrails.
- Do not submit abstract audience-intent sentences directly to low-control routes. Convert them into visible cues such as gaze direction, body angle, low/high position, exposed prop location, gun angle, light reflection, physical contact, and final posture.
- For 5-6 second or otherwise constrained tests, avoid combining three dense action phases, complex camera, long sound lists, many negative constraints, and narrative explanation. If camera is failing, make the next retry camera-first and reduce action detail.
- Iterate constrained-route prompts by one variable at a time: composition, body action, camera movement, prop/result, then sound. Do not rewrite every layer in one retry.
- For finished action sequences, generate each storyboard panel or clip segment separately, then stitch the clips in editing. Do not compress an entire multi-panel storyboard into one video generation call.
- Do not require upscale/repair before video generation unless a suitable model/tool is available and selected. If no repair/upscale route is configured, use the cropped single-panel reference directly after basic visual QC.

Website/app compiler additions:

- Treat this skill as a prompt compiler for production software, not as a one-shot string generator.
- For every renderable shot, output a structured compiler artifact with: `prompt_human_readable_zh`, `prompt_canonical_en`, `provider_execution_prompt`, `negative_constraints`, `api_params`, `asset_bindings`, and `qc_expectations`. A provider-specific alias such as `provider_execution_prompt` may be included only when that provider is selected.
- For combat shots, include the full Combat Pipeline artifact and validate against `schemas/combat_prompt_compiler_output.schema.json` or an equivalent app schema before generation.
- `api_params` should carry provider-confirmed technical controls such as model, route mode, duration, ratio/aspect_ratio, resolution, seed, generate_audio, return_last_frame, callback_url, watermark, camera_fixed, or quality mode. If a field is not confirmed for the selected provider, put it in `unverified_provider_fields` and do not rely on it.
- Keep prompt prose focused on visible content and motion. Do not use prompt prose as the only place where duration, ratio, resolution, seed, audio, return-last-frame, or watermark behavior is specified.
- Use `draft` mode for low-cost preview and A/B tests; use `final` mode for higher-quality routes when available and approved.
- Route policy: ordinary draft shots may use the lowest-cost route that passes the asset and QC gates. Complex/final battle shots require a route with enough reference, frame, duration, motion, and quality control for the shot. Escalate or switch routes after repeated failures caused by unclear space, invisible contact, VFX hiding action, false reaction, or prop drift.
- Production rendering must go through a backend Render Service, not direct browser/client calls. The service must create/retrieve/list/cancel tasks, handle webhook or polling idempotently, archive expiring provider URLs into owned storage, and record task metadata.
- Save prompt hash, compiler version, skill version, model id, provider, seed, params, input asset ids, task id, status, usage tokens, retry count, storage keys, and QC result for every generated clip.

## 9. Tool Route

Do not hardcode tool claims. Verify current:

- model ability
- price
- commercial terms
- platform specs
- account limits

Before choosing or using a route, ask or confirm the user's selected tools and models:

- image generation tool/model
- video generation tool/model
- audio or voice route/model, including whether every selected audio-capable video model has native dialogue/Foley enabled and foreground-only constraints set
- editing/rendering route
- resolution/cost mode
- whether to use a project model-route config or only tools named in the chat

A model-route config is optional and host-specific. Use the current project's documented config path when one exists; otherwise ask the user to confirm tools and models before generation.

If the config exists and contains enabled defaults, present the selected route to the user and ask for confirmation before generating assets or clips. If the user already named tools/models in the current request, restate those choices and confirm. Do not silently switch tools or models mid-project.

No image model is a built-in default. Use the best available user-approved image route for photos, still frames, starting frames, storyboard frames, character assets, scene assets, and prop assets. A deprecated video route does not automatically deprecate separate image-generation routes.

Never store raw API keys in project files, prompt packs, skills, or logs. Use environment-variable names from the model route config.

For all-project availability, prefer stable environment-variable names chosen by the project:

- `SHORTDRAMA_IMAGE_PROVIDER`, `SHORTDRAMA_IMAGE_MODEL`, `SHORTDRAMA_IMAGE_BASE_URL`, `SHORTDRAMA_IMAGE_KEY`
- `SHORTDRAMA_VIDEO_PROVIDER`, `SHORTDRAMA_VIDEO_MODEL`, `SHORTDRAMA_VIDEO_BASE_URL`, `SHORTDRAMA_VIDEO_KEY`
- `SHORTDRAMA_AUDIO_PROVIDER`, `SHORTDRAMA_AUDIO_MODEL`, `SHORTDRAMA_AUDIO_BASE_URL`, `SHORTDRAMA_AUDIO_KEY`

Provider credentials should live in the approved local secret store for the current host. Route labels should describe capability, not brand preference: `image_asset_route`, `video_draft_route`, `video_final_route`, `audio_voice_route`, `editing_route`.

At project start, read the configured model route file for the current host when one exists, then check only whether the required credentials or manual-access route exist. Never print raw key values in chat, logs, project files, prompt packs, or release files.

Do not ask the user to paste raw keys into chat unless there is no safer option. Prefer environment variables, OS keychain, provider CLI auth, or another approved secret store.

Default principle:

- avoid text-to-video as the main workflow when consistency matters
- prefer image-to-video, reference-to-video, multi-reference, character library, or subject library
- do not default to any single provider or local workflow
- if a shot needs multiple references, character plus scene references, prop references, first/end frames, video references, or audio references, choose a confirmed route with that capacity instead of forcing a weaker route

External creative-agent route:

- Treat å°äº‘é›€ / xyq and similar creative-agent platforms as optional tool routes, not as separate workflow authorities.
- Use them only when the user explicitly selects the platform for the current run or when the approved model-route config names it.
- Upload only assets that already passed the knowledge, asset, and QC gates.
- Submit the approved prompt package with exact reference-role labels. Do not let the platform rewrite, simplify, or bypass the pipeline's frame-phase, physical-logic, style, sound, and QC constraints unless the user approves a revised prompt.
- If the platform asks for intent confirmation, compare the confirmation against the approved prompt package before accepting it.
- Poll/download results as needed, then run the same image/video/audio/final QC. A platform success status is not a pipeline QC pass.

## 10. QC and Release

Run QC before release. Generate release package only after blockers are resolved.

Only video generation blocks require stopping immediately and returning to the nearest upstream stage. Still-image QC failures are regenerated and logged unless they involve real-person/celebrity/IP identity risk or require a user-approved story, character, or scene change.

Style drift created to bypass a rejection is a blocker. Resolve it by same-style repair, original-fictional-character redesign for identity-risk issues, or a user-approved full style migration with regenerated references.

Final render verification:

- Probe the release MP4 for resolution, duration, frame rate, video stream, and audio stream.
- Extract or view sample frames from opening, middle, climax/action, caption-heavy moments, transitions, and ending.
- Check for blank frames, frozen tail padding, watermark/UI/text leftovers, face obstruction, caption drift, mobile unreadability, and safe margins.
- Check final audio by listening through scene boundaries and the ending: dialogue sync, foreground Foley, duplicate audio, abrupt cuts, music climax alignment, and music fade/resolution.
- Captions should follow actual rendered audio timing from TTS word boundaries, final audio transcription, or manual waveform review. Do not rely only on script-time estimates.
- Save the result in `07_qc_report.md` before presenting the release file as finished.

Release package:

- titles
- descriptions
- tags
- cover copy
- pinned comments
- A/B testing plan
- compliance notes

## Default Workflow

1. Idea intake: capture idea, audience, platform, duration, style, business target, and forbidden zones.
2. Audience route: choose female-frequency, male-frequency, suspense, family, or another explicit route.
3. Story bible: protagonist goal, conflict, relationships, episode outline, hooks.
3A. Series engine: define the repeatable viewing promise, long-arc desire, per-episode payoff mechanism, pressure escalation, secret/evidence/payoff ledger, and episode-cluster reversals before writing a serious episode.
4. Director treatment and reference board: episode-level visual keywords, emotional curve, camera grammar, lighting/color route, editing rhythm, sound route, and 2-3 reference directions.
4A. Theme and mise-en-scene: convert the episode theme into visual motifs, power-space grammar, recurring composition rules, character psychology-to-space/light changes, and forbidden cheap emotion shortcuts.
5. Episode script: 0-3s hook, visible actions, dialogue, subtext, emotion beats, ending hook.
6. Character bible and asset packs: stable DNA plus four-view sheets, expression sheets, marker details, close-up references, performance notes, costume texture, and status symbols for every core character.
7. Scene bible and spatial packs: identifiable, repeatable locations plus 720-degree/multi-angle scene references, key camera positions, lighting states, material/prop texture, state variations, and prop close-ups.
7A. Prop and evidence ledger: track every repeated prop, proof object, identity marker, contract, phone, weapon, clue, or status object by owner, first appearance, viewer/character knowledge, physical state change, required close-up, post text plan, and reversal function.
8. Coverage, blocking, and performance plan: master/reaction/insert/transition coverage, actor movement paths, power-space relation, subtext, pauses, breath, gaze, reaction timing, scene objective, obstacle, tactic, beat changes, playable action verbs, emotional temperature, and reaction priority.
9. Cinematography bible (`04G_cinematography_bible.md`): aspect ratio, lens/focal rules, camera support, camera height, depth of field, movement limits, exposure/contrast, and shot-family continuity.
10. Storyboard: one shot equals one performable segment, with professional direction, frame phase plan, lens/camera/light/color/sound/editing intent.
11. Anime battle direction when applicable: for top-tier anime/donghua/xianxia battles, add animation timing, key poses, character combat styles, combo chains, FX bible, anime editing grammar, battle-space map, and layered generation plan before prompt writing.
11A. 3D donghua action layout when applicable: for top-tier 3D å›½æ¼« / 3D anime-style battles, add layout blocking, camera/character trajectories, animation mechanics, root motion, contact/IK notes, FX-light-compositing binding, battle asset state packs, and action readability QC before prompt writing.
12. Previs/animatic plan (`04H_previs_animatic_plan.md`): rough timing, shot duration, dialogue-to-picture fit, action continuity, edit rhythm, music/Foley cue placement, missing inserts, and generation-risk notes before prompt writing.
12A. Audience comprehension map (`04I_audience_comprehension_map.md`): prove what the viewer understands every 3 seconds, which clue or emotion each shot adds, what question the viewer should ask, how misdirection stays clear, and whether the scene remains readable when watched silently.
13. Prompt pack: still image prompts first, with separate starting-frame, storyboard/reference-frame, and ending-frame prompts, then 6s/10s/15s video prompts.
14. Tool route: choose image/video tools only after current capability, price, and commercial terms are verified.
15. Generation log: record inputs, assets, tools, results, failures, and retry actions.
16. Edit, color, and sound bible: character dialogue, performance timing, visible-source foreground Foley, deliberate silence, post-production music, color curve, rhythm map, transitions, and explicit background-sound exclusions.
17. QC: run hard gates before moving forward.
18. Release pack: title, description, tags, cover copy, pinned comment, A/B plan, compliance notes.
19. Postmortem: record retention, completion, comments, conversion, and next iteration.

For professional-level output, do not write generation-ready prompt packs before `04G_cinematography_bible.md` and `04H_previs_animatic_plan.md` exist and pass the delivery validator.

