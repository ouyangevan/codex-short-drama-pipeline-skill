# Project Package

Use this package shape for everyæµæ°´çº¿çŸ­å‰§ project.

## 00_knowledge_read_audit.md

Track knowledge-base intake before project generation:

- skill files read
- compiled knowledge files read from `knowledge_compiled/`
- minimum cache pass: relevant compiled cache files plus stage references inspected
- primary raw teaching files read only on cache miss, conflict, new material, or user-requested relearning
- `knowledge_cache_status`: `hit`, `partial_hit`, `miss`, or `conflict`
- `rg` searches performed and matched files only when raw teaching search is required
- transcript chunks or original-material sections opened for the current stage only when raw teaching search is required
- production stage gate entries: action about to be taken, relevant skill reference files opened, compiled cache files opened, stage-cache artifacts reused or invalidated, raw source sections opened when required, query terms used when required, and source rules applied before acting
- source status used for decisions: `approved_summary`, `transcribed_complete`, `visual_review_limited`, `unverified`, or `not_read`
- rules applied to the current output
- stage coverage matrix: idea, story, series engine, director treatment/reference board, theme/mise-en-scene, script, character, scene, prop/evidence ledger, production design, light/color, coverage, blocking/performance, actor rehearsal, lens/camera, storyboard, frame phase plan, audience comprehension, prompt, generation, editing rhythm, sound director, edit, QC, release; each stage must show `cache_status`, `compiled files used`, `stage_cache_hit/invalidated`, `raw_search_required`, and `not_read` if not covered
- per-stage cache proof: before each stage artifact is generated, list the compiled cache files, stage references, reused stage-cache artifacts, and the rules copied into the stage constraints
- pre-output compliance check per stage: immediately before the artifact, prompt, generation call, edit, QC conclusion, or release package is produced, list cache files checked, rules checked, pass/fail result, revisions made, and final approval to proceed
- source-backed rule list: every major workflow or prompt rule used in generated artifacts must name the local source file or be marked as skill-only
- delivery gate record for every stage artifact and generated output:
  - `knowledge_gate`: `PASS` only with stage name, compiled cache files or required raw source files, rules applied, stage-cache reuse decision when applicable, and `pre_output_compliance_check`
  - `asset_gate`: `PASS`, `FAIL`, or `N/A`
  - `qc_gate`: `PASS`, `FAIL`, `QC_UNVERIFIED`, or `N/A`
  - `allowed_output`: `deliverable` or `blocked_report_only`
- unknowns, missing access, outdated tool claims, or facts needing live verification

Do not write "fully read the whole database" unless a full chunked re-audit has been completed and saved as an external report file. A quick startup pass is not enough to create project artifacts.

Update this audit at project initialization, when a new stage starts, when cache miss/conflict requires raw source search, when new teaching material is added, or when the user requests relearning. Do not run a full audit for every shot or prompt wording change inside an already audited stage. If there is no stage-start cache evidence, do not proceed to the artifact.

If a project stage is marked `not_read`, do not generate that stage's output. Read the relevant compiled cache and references first; search raw knowledge-base sections only when the cache misses or conflicts, then update the audit.

If a stage artifact exists without per-stage cache proof or required raw-source proof, mark it invalid and redo the stage after reading the cache or required database sections.

If a prompt pack, generation call, edit, QC conclusion, or release artifact exists without a passing pre-output compliance check, mark it invalid and revise/recheck before generation or delivery.

If any stage has `allowed_output: blocked_report_only`, do not present its artifact, image, clip, edit, or release file as a usable result. Deliver only the blocker report, the failed gate, the violated source-backed rule, and the next retry route.

Every user-facing stage delivery must start with:

```text
Gate Status:
- knowledge_gate: PASS/FAIL
- asset_gate: PASS/FAIL/N/A
- qc_gate: PASS/FAIL/QC_UNVERIFIED/N/A
- allowed_output: deliverable|blocked_report_only
```

Before delivering a package stage, run the local delivery validator configured for the current host when one exists. If no executable validator is configured, record `executable_gate: N/A` and rely on the documented gate evidence.

Save or summarize the validator result in `00_knowledge_read_audit.md`. A failed validator result overrides the agent's own judgment.

## stage_cache/

Use `stage_cache/` to store reusable stage snapshots:

- `stage_cache/story_bible.md`
- `stage_cache/character_bible.md`
- `stage_cache/scene_bible.md`
- `stage_cache/cinematography_bible.md`

If the project already has a valid cached bible and no material upstream change has occurred, reuse it instead of regenerating. Record `stage_cache_hit`, dependency check, and reuse decision in `00_knowledge_read_audit.md`.

Invalidate the relevant cache when story premise, character DNA, scene anchors, visual style, route/model capability, camera grammar, or a downstream QC failure proves the cached artifact is unsafe.

## render_compiler/

Use this folder when the skill is being used as website/app logic or when a shot will be sent to a video provider.

Required files:

- `prompt_compiler_output.json`: structured compiler artifact for the current shot or batch.
- `combat_prompt_compiler_output.json`: required for any single combat shot before video prompt or render task creation.
- `combat_prompt_compiler_sequence.json`: required when a combat example or package contains multiple shot compiler outputs under one sequence object.
- `combat_prompt_compiler_output.schema.json`: copy or reference `schemas/combat_prompt_compiler_output.schema.json` when the project uses the Combat Pipeline for single shots.
- `combat_prompt_compiler_sequence.schema.json`: copy or reference `schemas/combat_prompt_compiler_sequence.schema.json` when the project uses multi-shot combat sequence packages.
- `render_task_log.jsonl`: one line per provider task submission, retry, callback, poll result, archive action, and QC decision.
- `provider_capability_matrix.md`: verified provider/model fields and unverified fields. Do not assume fields from another provider.
- `asset_binding_manifest.json`: asset ids, local paths/storage urls, provider file ids if any, role labels, rights status, phase labels, and expiry.

`prompt_compiler_output.json` must include:

```json
{
  "project_id": "",
  "episode_id": "",
  "shot_id": "",
  "render_mode": "draft|final",
  "provider": "",
  "model": "",
  "skill_version": "",
  "prompt_compiler_version": "",
  "prompt_hash": "",
  "prompt_human_readable_zh": "",
  "prompt_canonical_en": "",
  "provider_execution_prompt": "",
  "negative_constraints": [],
  "api_params": {
    "duration": null,
    "ratio": "",
    "resolution": "",
    "seed": null,
    "generate_audio": false,
    "return_last_frame": true
  },
  "unverified_provider_fields": {},
  "asset_bindings": [],
  "qc_expectations": []
}
```

For combat shots, `combat_prompt_compiler_output.json` or `combat_prompt_compiler_sequence.json` is required and must be validated before generation. The user-facing Chinese prompt may explain the intent, but the provider execution prompt must be compiled from visible evidence: spatial relation, tactic, contact/collision, impact feedback, reaction, end state, camera coverage, VFX attachment, and short negative constraints.

Fight repair records must include:

```json
{
  "failure_reason": "action_overload|missing_contact_visibility|unclear_spatial_axis|reaction_not_bound_to_contact|vfx_occludes_action|camera_competes_with_action|prop_binding_missing|style_conflict|model_route_too_weak",
  "what_to_remove": [],
  "what_to_keep": [],
  "revised_shot_graph": {},
  "revised_provider_execution_prompt": "",
  "revised_api_params": {}
}
```

Render task records must track:

- `task_id`, `provider`, `model`, `status`, `created_at`, `updated_at`
- `project_id`, `episode_id`, `shot_id`, `prompt_hash`, `seed`, `retry_count`
- `input_asset_ids`, `api_params`, `provider_payload_redacted`
- `video_url_expiry_risk`, `last_frame_url_expiry_risk`
- `storage_key_video`, `storage_key_last_frame`
- `usage.completion_tokens`, `usage.total_tokens`, cost estimate when available
- `qc_gate`, `review_status`, `human_qc_score`

Provider URLs are temporary assets. On success, download and persist video and last frame to owned storage before presenting them as project assets.

For any combat shot, `combat_prompt_compiler_output.json` must include:

- `style_route`: `3d_guoman_cinematic`, `2d_ink_anime_high_impact`, or `live_action_blockbuster_fight`
- `fight_director`: fight intent, combatants, tactical objective, counter-pressure, spatial map, action chain, result state, risk level, readability plan
- `combat_beat`: beat type, screen action, tactical meaning, anticipation, contact/collision, impact feedback, reaction, aftermath, camera logic, VFX logic, continuity out
- `impact_system`: impact level, pre-impact, contact frame, hitstop, recoil, environment feedback, sound hint, aftermath pose
- `vfx_power`: VFX type, source, shape, motion, color, body/environment interaction, visibility rule, start/peak/end state
- `camera_coverage`: shot type, distance, lens feel, motion, screen direction, subject priority, cut point, continuity in/out
- `provider_route_strategy`: full vs fast route, duration, complexity, references, first/end frame plan, prompt compression rule
- `combat_qc_score`: 0-5 scores for action readability, tactical clarity, contact believability, impact feedback, spatial continuity, VFX readability, style consistency, and cutability

If any combat QC score is below 4, do not create the render task.

## 00_idea.md

- original idea
- target audience
- target platform
- duration
- visual style
- commercial target
- forbidden zones
- risk screen

## 01_story_bible.md

- one-line sell point
- world and era
- protagonist goal
- core conflict
- character relationships
- episode outline
- visual asset needs
- risks

## 01C_series_engine.md

Required for repeatable series packaging:

- viewing promise: why the audience returns every episode
- long-arc desire separate from the single-episode goal
- per-episode payoff mechanism: emotional value, çˆ½ç‚¹, suspense, romance pull, humiliation reversal, proof reveal, or fear
- pressure escalation ladder across episodes
- secret/evidence/payoff ledger: planted information, who knows it, who misreads it, and when it pays off
- 3-episode, 5-episode, and 10-episode cluster reversal targets when relevant
- audience knowledge state: what the audience knows vs what characters know

If missing, label professional series packaging `series_engine_not_ready`.

## 01A_director_treatment.md

Required for professional-level output:

- episode visual promise
- emotional curve
- genre camera grammar
- rhythm style
- color/light route
- sound route
- performance tone
- what the finished video should feel like
- what must not be copied or imitated

## 01B_reference_board.md

Use 2-3 reference directions. For each, record:

- reference purpose: camera grammar, lighting, color, performance tone, editing rhythm, production design, or VFX scale
- what to borrow
- what not to copy
- copyright/IP/likeness/music risk
- how the reference is translated into original short-drama rules

## 01D_theme_and_mise_en_scene.md

Required for professional-level output:

- theme statement
- visual motifs and repeated objects/images
- power-space grammar: high/low, center/edge, blocked/open, near/far, reflected/direct, inside/outside
- psychology-to-space/light conversion
- composition motif and reversal plan
- forbidden cheap emotion shortcuts: crying without action, yelling instead of tactic, unmotivated slow motion, explanatory dialogue replacing behavior

Theme must affect blocking, light, props, composition, and performance. If missing, label professional storyboard/prompt stages `theme_mise_en_scene_not_ready`.

## 02_character_bible.md

Table columns:

`character | age | face/features | hair | body | outfit | marker | default expression | relationship role | aesthetic check`

Also include character asset pack requirements:

- four-view sheet
- expression sheet
- marker detail sheet
- close-up reference

## assets/character_packs/

One folder per core character. Include four-view, expression, marker detail, and close-up references. Single glamour portraits do not satisfy this package.

## 03_scene_bible.md

Table columns:

`scene | story purpose | time/weather | spatial structure | key props | atmosphere | light | angle/state versions`

Also include scene spatial asset pack requirements:

- 720-degree/multi-angle references
- key camera positions
- state variations
- prop close-ups

## assets/scene_packs/

One folder per core scene. Include 720-degree/multi-angle references, key camera positions, state variations, and prop close-ups. Single mood images do not satisfy this package.

## 03C_prop_and_evidence_ledger.md

Required when props, clues, proof objects, contracts, phones, messages, identity markers, weapons if allowed, or status objects affect causality or reversal.

Table columns:

`prop/evidence | visual identity | story function | owner/handler | who sees it | who misreads it | first appearance | payoff shot | physical state changes | required closeups | text/screen post plan | continuity risks`

Rules:

- A reversal cannot depend on a prop or evidence object the audience never clearly saw.
- Readable legal documents, phone UI, announcement screens, messages, and evidence text should be blank/unreadable in generation and added in post unless a confirmed route can safely control text.
- Repeated props need independent prop references plus character-bound scale/grip/use-state references when handling matters.

## 03A_production_design_texture.md

Track professional texture:

- costume material, fit, aging, status symbols
- hair/makeup state
- prop symbolism and use state
- set dressing, wear, cleanliness, class signal
- material close-ups needed for generation
- what changes after conflict or impact

## 03B_light_color_script.md

Track:

- episode color arc
- scene palette
- practical light sources
- light direction and contrast
- warm/cold shifts
- shadow and silhouette plan
- highlight/rim/reflection strategy
- darkness or reveal plan
- color change at hook, reversal, climax, and ending

## 04A_coverage_plan.md

For every scene, list:

- master/spatial shot
- clean singles
- over-shoulder shots
- reaction shots
- inserts and proof/object close-ups
- atmosphere or transition shots
- safety shots for editing
- which shots are essential and which are optional backups

## 04B_blocking_and_performance.md

For every scene and key shot, list:

- character movement path
- power position and distance
- who approaches, retreats, blocks, or reveals whom
- eye-line and prop handoff
- subtext and line intention
- pause, breath, gaze shift, micro-expression
- restraint/explosion point
- reaction timing
- continuity state after the beat
- scene objective: what the character is trying to get in this scene
- obstacle: who or what blocks the objective
- tactic: how the character tries to win the beat, such as charm, threat, silence, bait, lie, expose, retreat, or sacrifice
- beat changes: line or action where the character changes tactic
- playable action verbs: actions an actor can play, such as test, corner, seduce, suppress, hide, confess, provoke, protect, or dismantle
- emotional temperature curve from 0-10
- reaction priority: whose reaction carries the shot, even if another character is speaking

## 04C_frame_phase_plan.md

Required before generating starting frames, storyboard/reference frames, ending frames, or video prompts.

For each shot, list:

`shot id | causal action | starting_frame_phase | storyboard_reference_phase | ending_frame_phase | physical_transition | missing_intermediate_frames | invalid_frame_reuse_risk`

Rules:

- starting frame = pre-action setup or exact first controllable state before the cause completes
- storyboard/reference frame = representative middle action or composition guide
- ending frame = result/aftermath
- if a storyboard/reference frame or ending frame is reused as a starting frame, mark the prompt invalid
- if the transition is too large, create intermediate frames or split the shot

Glass slip example:

- starting frame: the glass is still in the character's hand; fingers are loosening; liquid is still inside
- storyboard/reference frame: the glass is halfway through falling; motion direction clear; hand above, floor/table below
- ending frame: glass shards and liquid are scattered on the floor/table; impact aftermath is visible

## 04_storyboard.md

Table columns:

`shot id | shot type | coverage role | duration | dramatic function | visual intent | scale class | viewer attention | shot size | composition hierarchy | lens/camera language | camera motivation/movement | transition design | lighting design | color note | depth design | reveal path | scene id | character | screen position | body state | blocking movement | prop state | action phase | action | expression/performance note | environment/VFX response | dialogue/subtext | sound | frame phase plan | still notes | video notes | previous state | start/end frame rule | continuity`

Shot type must be one of:

- single shot
- multi-shot
- nine-grid
- insert
- reaction
- transition

Continuity fields must say where each important character and prop starts, what changes during the shot, and what state must carry into the next shot.

Every shot must include a professional direction pass: dramatic function, viewer attention, camera motivation/movement, transition design, lighting design, depth design, and rhythm. Generic camera labels such as "medium shot", "slow push-in", or "cinematic lighting" are invalid unless they explain what the camera/light changes for the viewer.

For spectacle, fantasy, Eastern-aesthetic large scenes, or VFX battle shots, the storyboard must include a visual-director pass. If it only describes character positions and actions without scale, foreground/midground/background, camera motivation, reveal path, or environment response, mark the shot invalid before prompt writing.

Every combat shot must include a combat dynamics pass: pressure, tension, speed cue, power transfer, impact result, resistance, and aftermath. This applies to close combat, weapon combat, chase/ambush attacks, supernatural fights, VFX battles, and any strike or clash shot.

## 04D_lens_camera_language.md

Track per shot or shot family:

- lens feeling: wide, normal, telephoto/compressed, macro/detail, aerial/drone-like, handheld, stabilized, tracking, locked-off, or surveillance-like
- camera height and distance
- depth of field
- spatial compression or expansion
- whether the lens choice supports intimacy, pressure, scale, suspicion, comedy, or impact

## 04G_cinematography_bible.md

Required for professional-level output. This file turns scattered lens notes into a consistent episode camera system.

Track:

- `aspect_ratio_and_framing`: target aspect ratio, safe frame, close-up rules, headroom, negative space, and mobile-readable composition
- `lens_package`: wide, normal, telephoto/compressed, macro/detail, aerial/drone-like, handheld/stabilized/tracking/locked families, and when each is allowed
- `focal_length_rules`: which character, power state, scene type, or story beat gets wide, normal, compressed, macro/detail, or aerial feeling
- `camera_support_rules`: locked-off, handheld, stabilized, tracking, crane/drone-like, orbit, push/pull, whip-pan, and forbidden overused moves
- `camera_height_power_rules`: eye level, low angle, high angle, overhead, ground level, shoulder level, and how height expresses status, intimacy, pressure, vulnerability, or scale
- `depth_of_field_strategy`: deep focus, shallow focus, rack focus, foreground occlusion, reflection, and what each reveals or hides
- `exposure_contrast_texture`: high/low key, silhouette, rim/back light, flare, reflection, shadow density, highlight control, and practical-light logic
- `movement_restrictions`: camera moves that must not be overused, genre-specific limits, and when a locked frame is stronger than movement
- `shot_family_continuity`: recurring camera grammar for protagonist, antagonist, romance, humiliation, power entrance, action, proof inserts, and cliffhangers

If this file is missing, label professional prompts `cinematography_not_ready`.

## 04E_anime_battle_direction.md

Required when the project contains top-tier anime battle, donghua/anime-style combat, stylized xianxia action, or any fight whose quality depends on animation timing, key poses, combo continuity, and FX language.

Track:

- `animation_timing_chart`: anticipation, hold, acceleration, impact frame, recoil, follow-through, recovery, smear frame, and impact-frame hold if used
- `key_pose_sheet`: start pose, wind-up pose, burst pose, contact pose, hit reaction pose, aftermath pose, readable silhouette, line of action, limb/weapon direction
- `character_combat_style`: each fighter's combat personality, movement rhythm, preferred distance, attack route, defense habit, signature weapon/energy shape, weakness
- `combo_chain`: probe, evade, counter, guard break, chase, reversal, finisher, interruption, cliffhanger
- `anime_fx_bible`: FX shape language, color, edge style, motion trail, speed lines, aura, sparks, smoke, dust, debris, shockwave, magic circle, lightning/fire/water/weapon energy behavior
- `anime_editing_grammar`: stillness-to-burst, cut-in, reaction cut, impact frame, speed-line wipe, black-frame hit, match-on-action, foreground wipe, fast insert, silence hold, hold/release rhythm
- `battle_space_map`: character positions, distance, height, ground/air state, axis, camera side, attack direction, retreat path, obstacles, destructible terrain, and terrain changes after each exchange
- `layered_generation_plan`: layout, key pose, action timing, FX, camera, impact, sound, and continuity layers

This file is a blocker for top-tier anime battle prompts. If it is missing, label the project `anime_battle_not_ready` and do not produce generation-ready fight prompts.

## 04F_3d_donghua_action_layout.md

Required when the project targets top-tier 3D å›½æ¼«, 3D anime-style battle, cinematic xianxia 3D combat, stylized CG martial action, or any fight whose quality depends on 3D layout, animation mechanics, FX-light integration, and action readability.

Track:

- `layout_blocking_map`: terrain coordinates, character start/end positions, height levels, camera side, screen direction, axis rule, reset points, and safe spatial anchors
- `camera_character_trajectory`: camera path, character path, parallax layers, foreground/midground/background crossing, occlusion/reveal points, speed changes, and camera stop/readability points
- `animation_mechanics`: center of gravity, root motion, foot planting, hip/shoulder rotation, weapon arc, landing buffer, recoil, follow-through, balance recovery, and secondary motion for hair/cloth/sleeves/ribbons/armor/accessories
- `contact_and_ik_notes`: hand/weapon grip, foot-ground contact, collision point, shield/weapon contact, body penetration risks, prop scale, left/right limb control, and crop/occlusion plan for risky contact
- `fx_light_compositing_binding`: light spill, shadow, reflection, silhouette occlusion/reveal, foreground/background FX layers, smoke/dust/debris, aura, sparks, shockwave, magic circle, and weapon trail interaction with characters and set
- `battle_asset_state_pack`: combat outfit state, weapon states, energy-form turnarounds, damage/dirty states, facial strain, scene destruction states, debris assets, and before/mid/after environment variants
- `action_readability_qc`: readable silhouette, clear attack line, visible anticipation, impact frame/hitstop, contact/result clarity, no motion blur over key pose, no camera shake hiding the strike, and clear winner/loser state after the exchange

This file is a blocker for top-tier 3D donghua battle prompts. If it is missing, label the project `3d_donghua_action_not_ready` and do not produce generation-ready 3D battle prompts.

## 04H_previs_animatic_plan.md

Required before professional prompt writing. This file proves the episode can cut, sync, breathe, and land before spending generation credits.

Track:

- `rough_timeline`: shot order, estimated duration, hold points, speed changes, and total scene/episode duration
- `dialogue_picture_fit`: which line is on-screen, off-screen, over reaction, over insert, or split across shots; lines too long for the usable picture
- `action_continuity_check`: motion, screen direction, prop state, body position, eyeline, and impact aftermath across cuts
- `edit_rhythm_map`: stillness, fast cuts, reaction holds, inserts, proof shots, silence, music hits, and hard cuts
- `music_foley_cue_map`: dialogue, foreground Foley, silence, risers, hits, music phrase points, and places where sound must bridge across cuts
- `missing_insert_list`: objects, hands, reactions, atmosphere, proof shots, transition shots, safety shots, and cutaways needed to make the edit work
- `generation_risk_map`: high-risk shots, likely model failures, split/regenerate strategy, backup insert plan, and max retry budget
- `animatic_decision`: pass, revise storyboard, split shot, add insert, shorten dialogue, change camera, regenerate asset, or block

If this file is missing, label professional prompts `previs_not_ready`.

## 04I_audience_comprehension_map.md

Required before professional prompt writing.

Track:

- `three_second_knowledge_beats`: what the viewer must understand or feel every 3 seconds
- `shot_information_delta`: what each shot adds: fact, proof, emotional shift, relationship change, danger, misdirection, or payoff
- `viewer_question_track`: what question the viewer should be asking after each beat
- `clue_vs_emotion_split`: which elements prove facts and which create feeling
- `misdirection_clarity`: what is intentionally hidden while basic action remains clear
- `silent_watch_readability`: whether the scene still reads with sound off through action, blocking, props, expression, and post captions/text
- `reversal_setup_payoff_check`: where the ending reversal was visibly planted and how it pays off

If this file is missing or silent-watch readability fails, label professional prompts `audience_comprehension_not_ready`.

## 05_prompt_pack.md

Include:

- source inheritance block: which series engine, director treatment, reference board, theme/mise-en-scene, prop/evidence ledger, coverage plan, blocking/performance, actor rehearsal, lens/camera, cinematography bible, light/color, production design, editing rhythm, sound-director, previs/animatic, and audience comprehension rules constrain this prompt
- frame phase plan per causal action shot
- separate starting-frame, storyboard/reference-frame, and ending-frame prompts when a shot has physical progression
- professional direction pass per shot: dramatic function, viewer attention, camera motivation/movement, transition design, lighting design, depth design, rhythm, and generic-camera negatives
- cinematography bible inheritance: aspect ratio/framing, lens package, focal length rule, camera support, camera height power rule, depth of field, exposure/contrast texture, movement restriction, and shot-family continuity
- previs/animatic inheritance: rough timing, dialogue-picture fit, action continuity, edit rhythm, music/Foley cue, missing inserts, generation risk, and animatic decision
- audience comprehension inheritance: three-second knowledge beats, shot information delta, viewer question, clue/emotion split, misdirection clarity, silent-watch readability, and reversal setup/payoff check
- visual-director pass per spectacle or high-impact shot: visual intent, scale class, composition hierarchy, camera motivation, reveal path, environment/VFX response, and flatness negatives
- combat dynamics pass per combat shot: pressure_visualization, tension_visualization, speed cue, power transfer, impact result, resistance, aftermath, and combat flatness negatives
- pressure_visualization must describe how camera, composition, blocking, lens, scale, light, and screen space create oppression; do not use it only to say who suppresses whom
- tension_visualization must describe how camera, composition, timing, coiling, occlusion, distance compression, and imminent release create action tension; do not use it only to say what may break
- anime battle direction inheritance for top-tier anime fights: animation timing chart, key pose sheet, character combat style, combo chain, anime FX bible, anime editing grammar, battle space map, and layered generation plan
- 3D donghua action layout inheritance when applicable: layout blocking map, camera/character trajectory, animation mechanics, contact/IK notes, FX-light-compositing binding, battle asset state pack, and action readability QC
- still prompt per shot
- English prompt where useful
- negative prompt
- video prompt per shot
- ending state
- reference binding map per generation: image order, asset purpose, and whether each image is a start frame, end frame, character reference, scene reference, prop reference, expression reference, or storyboard reference
- action phase binding map per generation: each uploaded image must say pre-action setup, middle-action/reference, result/aftermath, character reference, scene reference, prop reference, expression reference, or motion reference
- control-layer priority per generation: identity, scene, prop, start/end state, motion reference, audio reference, and which layer is intentionally sacrificed if the selected model route cannot support all of them
- motion reference plan for action/fight/dance/VFX/impact shots: legal source status, what to reference, trimmed duration, beat timing, and non-copy rule
- low-cost preflight result before expensive generation: reference roles, frame phases, timing density, physical transition, character/scene consistency, style consistency, sound layer, and QC blockers checked
- sound layer per video prompt: dialogue/open-mouth state, visible-source foreground Foley/emphasis sounds, deliberate silence, forbidden background bed, and post-production fallback. For any confirmed native dialogue/Foley route, mark background ambience, room tone, banquet-hall chatter, indistinct party conversation, crowd murmur, music, BGM, songs, and soundtrack beds as `none`.

## 05A_editing_rhythm_map.md

Track:

- hook cut rhythm
- fast/slow segments
- hold points and silence beats
- reaction durations
- proof insert timing
- transition plan
- speed ramps or freeze-frame prohibition
- music climax alignment
- ending hook cut and fade/black-screen plan

## 05B_sound_director_layer.md

Track:

- voice performance per character
- dialogue timing and emotion
- foreground Foley priority
- silence design
- music entry/exit and climax point
- risers, hits, impacts, whooshes if used
- sound bridges between shots
- generated native audio route rules
- forbidden background bed and ambience exclusions

## 06_generation_log.md

Track:

- tool
- input assets
- output files
- result judgment
- problem
- retry action

## 07_qc_report.md

Track:

- story
- hook
- character
- scene
- video
- audio
- foreground/background audio separation
- subtitles
- dialogue/voice sync
- duplicate audio
- track linking
- speed changes
- tail-frame freeze
- first-frame AI label or watermark
- leftover UI/text
- mobile readability
- final render technical probe: resolution, duration, fps, video stream, and audio stream
- final render sampled-frame checks: opening, middle, climax/action, transition, caption-heavy moment, and ending
- final audio listen-through: dialogue sync, foreground Foley, duplicate audio, abrupt cuts, music climax alignment, and ending fade/resolution
- caption timing source: TTS word boundaries, final audio transcription, or manual waveform review
- compliance
- blockers
- rework list

## 08_release_pack.md

Include:

- titles
- descriptions
- tags
- cover copy
- pinned comments
- A/B test
- compliance notes
- platform verification notes

## Required Output Package

For each new short-drama project, create or update:

- `00_knowledge_read_audit.md`
- `stage_cache/` with reusable story, character, scene, and cinematography bible snapshots when valid
- `00_idea.md`
- `01_story_bible.md`
- `01C_series_engine.md`
- `01D_theme_and_mise_en_scene.md`
- `02_character_bible.md`
- `03_scene_bible.md`
- `03C_prop_and_evidence_ledger.md`
- `assets/character_packs/` with four-view sheets, expression sheets, marker details, and close-up references for core characters
- `assets/scene_packs/` with 720-degree/multi-angle references, key camera positions, state variations, and prop close-ups for core scenes
- `04_storyboard.md`
- `04E_anime_battle_direction.md` when applicable
- `04F_3d_donghua_action_layout.md` when applicable
- `04I_audience_comprehension_map.md`
- `05_prompt_pack.md`
- `06_generation_log.md`
- `07_qc_report.md`
- `08_release_pack.md`

Load `references/workflow.md` for stage rules. Load `references/prompt-rules.md` before writing prompts. Load `references/qc-gates.md` before saying a project is ready. Load `references/boundaries.md` when skill selection is ambiguous.

