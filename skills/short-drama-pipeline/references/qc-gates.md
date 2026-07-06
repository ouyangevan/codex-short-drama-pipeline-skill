# QC Gates

Route blockers by media type.

- Non-delivery rule: a blocker is not a warning. If any required QC blocker fails, or if the output has not been visually/audibly inspected, set `qc_gate` to `FAIL` or `QC_UNVERIFIED` and set `allowed_output` to `blocked_report_only`.
- Do not deliver a failed or unverified image/video/audio edit as a usable result. It may be referenced only as failed evidence with a fix route and retry plan.
- Missing four-view/expression/marker/close-up packs for core characters and missing 720-degree/multi-angle spatial packs for core scenes are hard blockers before serious video generation.
- A generated asset or clip that has not been checked against this file cannot be used as a starting frame, ending frame, character reference, scene reference, prop reference, storyboard reference, final clip, or release asset.

- Video generation blockers return the project to the nearest upstream stage and require user confirmation before continuing.
- Still-image blockers for photos, storyboard frames, character assets, scene assets, and prop assets can be retried directly with a compliant prompt while preserving approved story, character, scene, and prop facts. Log the failure, changed prompt/visual handling, retry count, output file, and QC result. Explain what went wrong and what changed after the batch or shot is completed.
- Still-image retries must stop only when the issue involves real-person/celebrity/IP identity risk, unsafe/noncommercial content that cannot be safely reframed, or any change to approved story causality, character identity, or scene facts.

## Character Blockers

- unlicensed likeness or copyrighted character
- platform rejects a character/reference image as a real person, celebrity likeness, face imitation, or identity-risk asset
- missing character DNA
- missing four-view sheet for a core character before serious video generation
- missing expression sheet for a core character used in close-ups or reaction shots
- inconsistent face, body, hair, or clothes
- target audience aesthetic failure
- bad proportions, bad hands, face collapse
- character/reference is changed to 2.5D, anime, sketch, pencil, oil-painting, or another style only because the model rejected it, while the approved project style remains realistic/live-action/CG

Real-person detection rule:

- Do not bypass platform real-person, likeness, or identity-risk detection.
- If a character/reference image fails platform detection, mark the shot as failed and return to character bible / character asset generation.
- Redesign the character as an original fictional character, regenerate the four-view sheet, expression sheet, marker details, and close-up references, then retry generation.

Style consistency rule:

- Model rejection does not authorize a partial style change.
- Repair rejected assets in the approved project style unless the user approves a full style migration.
- If style migration is approved, regenerate the affected character, expression, scene, prop, storyboard, and prompt references before continuing.

## Scene Blockers

- location not identifiable
- scene contradicts script
- missing 720-degree/multi-angle spatial references for a core scene before moving-camera or reverse shots
- key anchors do not match across scene angles
- no spatial depth or reverse-shot support
- missing continuity states
- text, watermark, UI, or subtitle in generated image
- scene/reference style drifts from the approved project style because a rejected image was converted into 2.5D, anime, sketch, pencil, oil-painting, or another isolated workaround

## Storyboard Blockers

- too many actions in one shot
- invisible psychology without visible behavior
- repeatable series episode lacks `01C_series_engine.md`, so the episode has no viewing promise, payoff mechanism, pressure escalation, or information/payoff ledger
- missing `01D_theme_and_mise_en_scene.md`, so theme does not affect blocking, light, props, composition, or performance
- professional-level production requested but missing director treatment, reference board, coverage plan, blocking/performance plan, lens/camera language, light/color script, production design texture, editing rhythm map, or sound director layer
- story reversal depends on a prop, clue, contract, phone, identity marker, or proof object that is missing from `03C_prop_and_evidence_ledger.md`
- missing establishing shot after time/place changes
- static reverse-shot overuse
- axis, position, or eye-line continuity is broken across shots
- adjacent shot sizes are cut together in a way that feels like an accidental jump instead of a deliberate emphasis
- the same camera angle is hard-cut to a similar angle without a clear emotional, spatial, or information reason
- dialogue coverage uses only repeated close-ups or medium close-ups without inserts, reaction shots, hand/prop details, wider spatial shots, or motivated cutaways
- impossible timing
- missing shot type route: single shot, multi-shot, storyboard sheet/grid, insert, reaction, or transition
- multi-panel storyboard generation lacks a full-sheet planning artifact when style/lighting/continuity need to be judged across the sequence
- missing screen position, body state, prop state, previous state, or start/end frame rule for a continuity-critical shot
- multi-shot prompt crosses scene ids, tracks too many characters, or combines dialogue/action that need separate timing
- missing professional direction pass: dramatic function, viewer attention, camera motivation, movement design, transition design, lighting design, depth design, or rhythm
- missing coverage role: master, clean single, over-shoulder, reaction, insert, proof/object, transition, atmosphere, VFX plate, or safety shot
- missing blocking or performance direction for a performance-heavy shot: movement path, power position, distance change, eye-line, subtext, pause, breath, gaze shift, micro-expression, or reaction timing
- missing actor rehearsal fields for a performance-heavy shot: scene objective, obstacle, tactic, beat change, playable action verb, emotional temperature, or reaction priority
- missing lens/camera language: camera height, lens feeling, distance, compression, depth of field, or handheld/stabilized/tracking/drone/locked-off intent
- missing lighting/color continuity from the light/color script
- missing production design texture when costume, prop, class/status, set material, or object state matters
- uses generic camera filler such as medium shot, close-up, slow push-in, cinematic lighting, or shallow depth of field without explaining what it reveals, hides, pressures, or changes emotionally
- missing visual intent, scale class, composition hierarchy, camera motivation, reveal path, or environment/VFX response for a spectacle, fantasy, Eastern-aesthetic, large-scene, or high-impact VFX shot
- treats left/right placement, standing poses, hand signs, or power direction as the full shot design instead of baseline continuity
- missing `04I_audience_comprehension_map.md` before professional prompt writing, or the shot has no information delta, viewer question, clue/emotion split, silent-watch readability check, or reversal setup/payoff check

## Professional Direction Blockers

- any shot's camera movement is decorative rather than motivated by reveal, concealment, power shift, intimacy, suspicion, comedy timing, impact, or emotional turn
- shot has no clear viewer-attention path: the eye does not know what to see first, second, and last
- transition is default or unexplained when the cut should carry emotion, information, rhythm, time jump, reaction, or impact
- lighting is generic and does not specify source, direction, contrast, color temperature, shadow, practical light, rim/back light, silhouette, reflection, or darkness reveal
- scene ignores available light logic: indoor practicals, window direction, street light, phone/screen light, candle/fire, neon, moonlight, sunset, or overcast softness
- every dialogue beat is covered with plain shot/reverse-shot or repeated medium close-ups without inserts, reactions, foreground occlusion, object evidence, wider pressure shots, or motivated cutaways
- power, romance, suspense, humiliation, comedy, grief, or reveal scenes use the same neutral camera grammar instead of genre-specific direction
- prompt can be fulfilled as a flat, evenly lit, front-facing recording of the action even though the story beat needs cinematic observation
- theme is stated as an abstract slogan but does not change mise-en-scene: blocking, light, prop, composition, distance, reflection, exposure, or power-space grammar

## Cinematic Visual Blockers

- shot fields are filled mechanically but do not express the user's requested cinematic feeling, scale, genre, or spectacle
- requested Eastern-aesthetic large scene lacks macro scale, foreground/midground/background layers, atmospheric depth, cloud/mist/light movement, or a near-to-far/low-to-high reveal
- requested colossal-form or god-form pressure shot keeps the form and human at similar visual weight instead of making the human small and the form dominant
- requested VFX battle becomes a flat stage-like two-character face-off, static equal left-right composition, simple beam collision, or pose-only spell casting
- camera movement is decorative and does not reveal new scale, power relation, spatial information, emotional pressure, or impact
- VFX has no environment response: no dust, cloud churn, robe movement, floor cracks, shockwave, light spill, debris, particles, or aftermath
- impact beat lacks a single clear collision/result moment, parallax, scale anchor, or reaction shot
- the prompt could be fulfilled by two ordinary people standing in an empty medium shot even though the user requested epic, cinematic, fantasy, xianxia, or high-impact visual effect

## Cinematography Bible Blockers

- missing `04G_cinematography_bible.md` before professional prompt writing
- prompt uses one-off lens/camera phrases without an episode camera system
- cinematography bible lacks aspect ratio/framing, lens package, focal length rules, camera support rules, camera height power rules, depth-of-field strategy, exposure/contrast texture, movement restrictions, or shot-family continuity
- every scene invents a different camera language without preserving character, genre, or shot-family continuity
- camera support is decorative: handheld, push-in, orbit, whip-pan, or drone-like movement is used because it sounds cinematic, not because it reveals information, pressure, scale, intimacy, or impact
- camera height does not express status, vulnerability, pressure, scale, or intimacy when the story beat depends on power relation
- lens choice fights the scene purpose, such as wide lens flattening an intimate confession, neutral eye-level shot weakening a power entrance, or telephoto compression hiding a necessary spatial relationship
- exposure, contrast, and light texture are generic and do not follow the light/color script or practical-light logic
- repeated movement creates visual sameness instead of a controlled camera grammar

## Combat Dynamics Blockers

- any combat shot lacks visual pressure, visual tension, speed cue, power transfer, impact result, resistance, or aftermath
- combat shot skips `combat_prompt_compiler_output.json` or equivalent structured compiler output before render
- combat prompt provides real-world fighting instruction, gore, explicit injury detail, or practical harm guidance instead of fictional screen choreography
- combat prompt uses a specific IP, character name, recognizable shot, or identifiable work/style as a direct imitation target
- `fight_final` shot lacks a structured shot graph with style profile, shot intent, spatial setup, start pose, primary action, contact target, reaction, end state, camera behavior, lighting, prop/asset bindings, VFX cues, negative constraints, and API params
- `fight_final` shot contains more than one tactical objective, more than two visible contact events, more than one major camera behavior, or more than one major VFX state shift without being split
- final battle route uses a low-control/fast route as final quality proof after failures caused by unclear space, invisible contact, VFX hiding action, false reaction, or prop drift, instead of escalating route, reducing scope with approval, or splitting the shot
- repair rewrites every layer at once instead of diagnosing one primary failure and preserving successful story, identity, scene, and control layers
- pressure is written only as narrative dominance, such as who suppresses whom, without camera/composition methods that make the character feel oppressive or visually crush the target
- tension is written only as a plot risk, such as what may break, without camera/composition/timing methods that make the action feel coiled, stretched, imminent, or about to release
- pressure lacks visible design such as low-angle dominance, foreground blocking, frame compression, looming silhouette, negative space, edge/bottom-of-frame squeezing, slow push-in, shadow fall, or scale imbalance
- tension lacks visible design such as held pause, diagonal attack line, extreme-foreground weapon/hand, shallow-focus distance compression, frame-edge threat, occluded danger, slow push before sudden motion, whip-pan anticipation, body coiling, or near-contact gap
- combat is described only as labels such as fierce fight, fast attack, power clash, beam collision, or two sides attacking each other
- strike has no wind-up, acceleration, contact or near-miss, recoil, environmental response, or reaction
- hit feels weightless because the target, shield, weapon, body, ground, air, water, or object does not resist before failing
- speed is claimed but not shown through motion blur, whip-pan, delayed reaction, dust trail, cloth snap, streaking debris, off-screen entry, sudden stop, or frame occlusion
- power is claimed but does not travel visibly through body mechanics, weapon vibration, energy compression, cracked ground, air distortion, shockwave, or object deformation
- impact has no exact contact point, result state, body recoil, debris, spark, crack, splash, sound cue, or changed posture
- close combat lacks body mechanics such as planted foot, hip/shoulder rotation, guarded face, blocked strike, grip pressure, breath, or follow-through
- weapon combat lacks attack line, parry angle, reach, sparks, vibration, grip pressure, footwork, or follow-through
- supernatural/VFX combat lacks force transfer, scale anchor, environmental deformation, pressure bending shields/air/clouds, or delayed debris fall
- VFX is named but not attached to a trigger, location, duration, action synchronization, environment response, and occlusion rule
- opponent reaction happens before contact, ignores the force direction, or does not change posture, balance, weapon/prop state, or battlefield relation
- avatar, domain, or suppression shot lacks scale contrast, such as small human, giant shadow, floor pattern, clouds, far silhouette, or foreground anchor
- weapon clash lacks collision, guard/parry, rebound, sparks/vibration, displacement, resistance, and changed result state
- strike exchange lacks contact point, body/cloth/dust/camera feedback, recoil, and aftermath pose
- constrained-route combat prompt carries multi-stage battle, multiple spell systems, avatar/domain plus weapon contact, or a whole storyboard sequence
- high-control/final combat prompt lacks first frame, key pose, end frame, or reference image plan when the shot depends on complex contact/VFX and the selected provider supports those controls

Combat QC scoring:

- Score `action_readability`, `tactical_clarity`, `contact_believability`, `impact_feedback`, `spatial_continuity`, `vfx_readability`, `style_consistency`, and `cutability` from 0 to 5.
- Any score below 4 blocks render. Rewrite the compiler output before creating provider tasks.
- Scores must cite visible evidence, not taste words such as cool, cinematic, intense, or epic.

## Anime Battle Direction Blockers

These blockers apply when the user asks for top-tier anime battle, donghua/anime-style combat, xianxia anime action, stylized 2D/2.5D/3D anime fighting, or premium animation impact.

- missing `04E_anime_battle_direction.md` before top-tier anime battle prompt writing
- anime battle prompt has ordinary combat dynamics but no animation timing chart: anticipation, hold, acceleration, impact frame, recoil, follow-through, recovery
- missing key pose sheet: start pose, wind-up pose, burst pose, contact pose, hit reaction pose, aftermath pose, readable silhouette, line of action, or limb/weapon direction
- every character fights with the same rhythm, range, posture, and attack logic because character combat style is missing
- fight is a set of disconnected single attacks instead of a combo chain with probe, evade, counter, guard break, chase, reversal, finisher, interruption, or cliffhanger
- FX are generic or inconsistent: energy, aura, magic circle, smoke, sparks, dust, debris, shockwave, speed lines, lightning/fire/water/weapon effects change randomly without a fixed anime FX bible
- anime editing grammar is missing: no stillness-to-burst, cut-in, reaction cut, impact frame, speed-line wipe, black-frame hit, match-on-action, foreground wipe, fast insert, silence hold, or hold/release rhythm
- battle space is unclear: no distance, height, ground/air state, axis, camera side, attack direction, retreat path, obstacles, destructible terrain, or terrain-change record
- action meaning is missing: character movements are named but their tactical purpose, character intention, viewer information delta, opponent counter-pressure, or power-state change is not defined
- character facing and spatial relation jump between shots: a character moves behind/around/under an opponent, but the next shot resets to face-to-face or another relation without visible turn, transition, match-on-action, reset shot, or spatial anchor
- prompt mixes layout, key pose, action timing, FX, camera, impact, sound, and continuity into one undifferentiated paragraph instead of a layered generation plan
- a full combo, camera move, pose change, FX explosion, dialogue, and environment destruction are compressed into one short video prompt without split shots or intermediate key frames

## 3D Donghua Action Layout Blockers

These blockers apply when the target is top-tier 3D 国漫, 3D anime-style battle, cinematic xianxia 3D combat, stylized CG martial action, or any fight whose quality depends on 3D layout, animation mechanics, FX-light integration, and action readability.

- missing `04F_3d_donghua_action_layout.md` before top-tier 3D donghua battle prompt writing
- 3D battle prompt inherits `04E_anime_battle_direction.md` but lacks layout blocking map, camera/character trajectory, animation mechanics, contact/IK notes, FX-light-compositing binding, battle asset state pack, or action readability QC
- layout is unclear: no terrain coordinates, height levels, camera side, screen direction, axis rule, reset point, or safe spatial anchor
- camera path and character path fight each other, so the viewer cannot read who moves where or what changes after impact
- animation mechanics are missing: no center of gravity, root motion, foot planting, hip/shoulder rotation, weapon arc, landing buffer, recoil, follow-through, balance recovery, or secondary cloth/hair/accessory motion
- contact/IK is unsafe: hand/weapon grip, foot-ground contact, collision point, shield/weapon contact, left/right limbs, prop scale, or body penetration risks are not controlled
- FX is pasted on top of the scene instead of integrated: no light spill, shadow, reflection, silhouette occlusion/reveal, foreground/background layering, smoke/dust/debris interaction, or aftermath state
- battle asset states are missing: combat outfit state, weapon states, energy-form turnarounds, damage/dirty states, facial strain, scene destruction states, debris assets, or before/mid/after environment variants
- action readability fails: silhouette is unclear, attack line is hidden, anticipation is skipped, impact frame/hitstop is missing, motion blur hides the key pose, camera shake hides contact, or winner/loser state is unclear
- prompt hides unreadable action behind bright FX, fast cuts, aggressive motion blur, or constant camera movement instead of splitting or simplifying the shot

## Previs And Animatic Blockers

- missing `04H_previs_animatic_plan.md` before professional prompt writing
- rough timeline is missing shot order, estimated duration, hold points, speed changes, or total duration
- dialogue-picture fit is missing, or a spoken line is longer than the usable picture without a planned reaction, insert, off-screen carry, line split, or rewrite
- action continuity is unproven across cuts: motion direction, prop state, body position, eyeline, impact aftermath, or screen direction does not carry
- start/end facing direction, body state, and spatial relation are not inherited from the previous shot or do not set up the next shot
- a repeated prop, cable, weapon, clue, or energy object appears in a shot without earlier visibility, owner/handler state, or spatial location
- edit rhythm is only described as fast/slow labels and does not map holds, reactions, inserts, proof shots, silence, music hits, hard cuts, or transition beats
- music/Foley cue map is missing, so dialogue, visible-source foreground Foley, silence, risers, hits, and music phrase points cannot be aligned
- missing inserts are treated as optional polish even though they are needed to hide model defects, carry dialogue, bridge action, or preserve continuity
- high-risk generation shots have no split/regenerate route, backup insert plan, or retry budget
- animatic decision is absent, vague, or says pass while unresolved timing, continuity, audio, or generation-risk blockers remain

## Motion Reference And Timing Blockers

- professional action, fight, dance, magic/VFX, fast camera, or impact-heavy shot has no motion plan and no legal/user-authorized motion reference when one is needed for the requested quality
- video reference role is unclear: the prompt does not say whether to use it for action, camera movement, rhythm, pose path, impact timing, or composition only
- a copyrighted, celebrity, film/TV/game, influencer, or music-video reference is treated as commercial source material without user ownership or clearance
- model route cannot combine the requested control layers, such as first/end frames plus video reference plus multiple character/scene references, but the prompt proceeds without naming the control priority and sacrificed layer
- action timing is too dense for the selected duration: more than 3 clear beats in 5 seconds, or more than 6 clear beats in 8-10 seconds, without split shots, intermediate frames, or a longer duration
- action beat lacks wind-up/threat, acceleration/pressure increase, contact/near-miss/result, recovery/recoil/environment response, or carry-forward state
- VFX attack lacks source, charge-up, release, travel path, impact point, environment response, sound cue, or aftermath
- prompt skips the low-cost preflight before expensive generation: reference roles, frame phases, timing density, physical transition, character/scene consistency, style consistency, sound layer, and QC blockers were not checked
- negative prompt or safety constraints are so broad that they remove the intended motion, impact, expression, environmental response, or visual force of the shot

## Physical Logic Blockers

- visible hand is reversed, malformed, missing fingers, has extra fingers, or grips an object impossibly
- left/right hand, screen direction, or character position contradicts the storyboard continuity map
- object floats, fuses with another object, penetrates the body/floor/table, or changes material without story cause
- start frame and end frame do not form a plausible physical transition
- ending/result image is being treated as the cause/start of the action
- action requires too many simultaneous body, prop, and camera changes for one short shot
- generated still or extracted frame already contains a physical error but is being reused as a reference

Fix route:

- split the action into setup, contact, impact/result, and reaction shots
- retry or locally redraw the bad area if story causality, character identity, and scene facts stay unchanged
- change camera design when a hand pose or physical contact keeps failing: occlude, crop, use over-shoulder, use object close-up, use reaction shot, or use a clean extracted frame from the previous clip
- do not pass a failed frame downstream as a starting frame, ending frame, character reference, scene reference, prop reference, or storyboard reference

## Prompt Blockers

- missing pre-output compliance check, or the check failed but generation/editing/delivery proceeded anyway
- prompt pack does not inherit constraints from series engine, director treatment, reference board, theme/mise-en-scene, prop/evidence ledger, coverage plan, blocking/performance plan, actor rehearsal, lens/camera language, cinematography bible, light/color script, production design texture, editing rhythm map, sound director layer, previs/animatic plan, and audience comprehension map
- prompt has no series-engine purpose: it does not serve the viewing promise, episode payoff mechanism, pressure escalation, secret/evidence payoff, or audience knowledge state
- prompt contains or depends on a prop/evidence object whose owner, handler, first appearance, physical state, close-up requirement, or post-text plan is not tracked
- prompt contradicts the prop/evidence ledger by changing object state, ownership, scale, text visibility, or payoff timing without an approved story change
- prompt lacks a playable performance tactic and beat change when the character is actively pursuing an objective
- prompt lacks audience-comprehension control: no 3-second knowledge beat, shot information delta, viewer question, clue/emotion split, silent-watch readability, or reversal setup/payoff
- fight/action prompt lacks action-meaning control: no protagonist tactic, opponent counter-action, viewer information delta, power-state change, or reason the chosen movement expresses character strategy
- constrained-route execution prompt contains uncompressed director reasoning, audience-intent explanation, excessive negative constraints, long sound lists, or too many simultaneous action/camera/prop goals for a short clip
- constrained-route retry has no clear primary variable, or changes composition, body action, camera, prop result, and sound all at once after a failure
- production website/app render request is only a prose prompt and lacks structured compiler output: human-readable prompt, canonical execution prompt, provider execution prompt, negative constraints, api_params, asset_bindings, and qc_expectations
- API controls such as duration, ratio/aspect ratio, resolution, seed, audio, return_last_frame, callback, watermark, or model route are only written inside the prompt prose instead of structured `api_params` when the provider supports them
- provider-specific fields are assumed from another provider without verification, such as treating Cloudflare/fal fields as confirmed Ark fields
- generated provider `video_url` or `last_frame_url` is treated as a permanent project asset without immediate owned-storage archival
- render task lacks prompt hash, compiler version, skill version, model id, provider, seed, params, input asset ids, task id, status, usage, retry count, storage keys, or QC result
- prompt is visually attractive but hides the proof object, confuses who knows what, or makes the current action unreadable without audio
- top-tier 3D donghua battle prompt lacks `04F_3d_donghua_action_layout.md` inheritance or omits layout, animation mechanics, contact/IK, FX-light-compositing, battle asset state, or action readability QC
- missing professional direction pass before prompt writing for any shot
- uses generic shot size, camera movement, transition, or lighting labels without dramatic function, viewer-attention path, motivated camera, transition design, lighting design, depth design, and rhythm
- missing visual-director pass before prompt writing for a shot that requires cinematic scale or spectacle
- uses shot size, composition, camera movement, or screen time as labels only, without visual intent, composition hierarchy, camera motivation, reveal path, and environment/VFX response
- missing combat dynamics pass before prompt writing for any fight, attack, chase attack, ambush, weapon clash, supernatural battle, or impact shot
- pronoun-only references
- hallucinated plot or props
- asks video model to generate text, UI, subtitles, watermark, or BGM
- provider asset handles such as `@image1` / `@video1` are uploaded without clear role labels such as character reference, scene reference, prop reference, start frame, end frame, action/camera reference, or authorized voice reference
- first/end frames do not form a plausible physical transition, or the gap should have an intermediate frame but none is provided
- four distinct storyboard beats are compressed into a 5-second generation without a strong reason and timing check
- storyboard assets for a multi-panel sequence are generated only as isolated mismatched panels when a full storyboard sheet was feasible, causing inconsistent style, lighting, character scale, or shot order
- a full multi-panel storyboard grid is uploaded as the reference for one video generation instead of cropping/selecting the intended panel or creating a dedicated frame reference
- an arrow-guide image is created from or uploaded as the full storyboard sheet instead of a duplicate of the cropped single panel/dedicated frame
- a finished multi-panel sequence is attempted in one video generation call instead of generating separate panel/clip segments and stitching them in editing
- the prompt uses a video reference longer or broader than needed without saying whether to reference only action, pose, rhythm, or camera
- for a confirmed native dialogue/Foley route, disables native audio without explicit user approval
- for a confirmed native dialogue/Foley route, lacks spoken dialogue instructions when the shot has character dialogue
- for a confirmed native dialogue/Foley route, lacks foreground diegetic sound/Foley for visible or story-focused actions such as glass shattering, forced door opening, pen movement, cup impact, chair scrape, footsteps, cloth, or breath
- for a confirmed native dialogue/Foley route, requests or outputs background ambience, room tone, crowd chatter, indistinct party conversation, or other non-story background noise
- for a confirmed native dialogue/Foley route, requests or outputs music, BGM, songs, lyrics, or soundtrack beds
- for a confirmed native dialogue/Foley route, fails to explicitly write the forbidden background bed as none: no banquet-hall chatter, no crowd murmur, no indistinct party conversation, no room tone, no music
- uses a weak one-image/text-only route as the default production route when the shot needs multiple references, character plus scene references, prop references, first/end frames, video references, or audio references
- uploaded image purpose is not labeled as starting frame, ending frame, character reference, scene reference, prop reference, or storyboard reference
- uploaded images are not mapped by order and role in multi-reference prompts
- image order and character names contradict each other
- repeated prop appears without a scale/use-state reference when size or handling matters
- more than one main scene reference competes in a single video prompt
- ending-frame image is used as the starting frame for a cause-and-effect action
- missing continuity state
- missing frame phase plan before generating starting frames, storyboard/reference frames, ending frames, or a cause-and-effect video prompt
- starting frame is actually a middle-action storyboard/reference frame, such as a glass already falling in midair when the action is "glass slips from hand"
- ending/result frame is reused as the starting frame for the cause of that result
- starting frame, storyboard/reference frame, and ending frame do not map to distinct causal phases when the action requires physical progression
- physical transition between starting frame and ending frame skips an essential intermediate phase but no intermediate frame or shot split is provided
- mixed multiple shots in one prompt
- treats a continuous combo as multiple actions solely because it contains repeated strikes; repeated slashes/punches are one combo beat when they share one tactical objective, spatial route, camera design, and result
- incomplete research source used as rule
- dialogue/dubbing is expected but the prompt lacks spoken line, speaker, emotion, or open-mouth/lip-sync state
- visible action has no matching sound or Foley plan when sound continuity matters
- prompt asks only one rejected asset or shot to use a different visual style from the approved project style without a user-approved full style migration

## Video Blockers

- face collapse or identity swap
- wrong action or wrong target
- continuity break
- random text, watermark, subtitle, or UI
- mouth/dialogue conflict
- unsafe or noncommercial content
- mixed visual styles across consecutive shots caused by rejection workaround rather than a planned full-series style choice

## Audio/Edit Blockers

- story unreadable
- no first 3s hook
- missing editing rhythm map for a professional-level output
- missing sound director layer for a professional-level output
- unclear audio copyright
- music covers dialogue
- music climax does not align with the picture climax and story climax when the edit is clearly trying to use music for impact
- music or ambience ends abruptly at a scene boundary or ending instead of resolving at a musical phrase, edit point, or fade-out
- missing expected sound
- missing visible-source foreground Foley for actions the audience can see, such as glass breaking, a forced door opening, a cup hitting the floor, a pen rolling, a chair scrape, footsteps, fabric movement, or breath
- generated clip contains unwanted background bed, banquet-hall chatter, crowd murmur, indistinct party conversation, room tone, generic ambience, music, BGM, songs, lyrics, or soundtrack beds
- duplicate audio: generated video voice plus post voice, doubled ambience, or repeated sound effect
- subtitle typo, wrong speaker, wrong language, or caption timing mismatch
- dialogue continues after the picture cuts away without a planned reaction/insert/continuation shot
- mouth is closed or wrong speaker is visible during a voiced line that should be on screen
- audio, captions, or overlays do not follow the edited video because track linking/magnetic timeline settings were wrong
- abrupt speed change or retiming calls attention to itself
- first frame contains AI label, watermark, UI, or unwanted generated text
- leftover on-screen text, model subtitles, platform UI, or watermark appears in the image/video
- mobile small-screen unreadability
- frozen last-frame padding used to cover dialogue or captions
- local/system TTS used as final overseas-release voice without emotion, pacing, pauses, and intonation control
- captions are timed from script estimates instead of actual audio timing from TTS word boundaries, final audio transcription, or manual waveform review
- more than one caption group remains visible at the same time, or old captions are not hard-cleared when the next caption starts
- final edit has not been probed for resolution, duration, frame rate, video stream, and audio stream before delivery
- final edit has not been spot-checked with extracted/viewed frames across beginning, middle, climax, and ending
- extracted frames show blank frames, text overflow, face obstruction, watermark/UI, unreadable mobile text, caption drift, or accidental frozen tail padding

## Final Render Blockers

- final MP4 or release file is delivered without a technical probe for resolution, duration, fps, video stream, and audio stream
- final MP4 is delivered without sampled frame inspection across opening, dialogue, action/climax, transition, caption-heavy area, and ending
- final audio is delivered without listening for abrupt scene-boundary cuts, duplicate voice/ambience, missing foreground Foley, music overpowering dialogue, or unresolved music ending
- caption timing is not based on actual rendered audio timing, such as TTS word-boundary timestamps, final narration transcription, or manual waveform review
- final rendered captions, overlays, character intro labels, black-screen CTA, or follow text are not checked for mobile readability and safe margins
- release candidate is missing a saved final-QC report that lists passed checks, failed checks, fixes, and remaining risks

## Release Blockers

- platform policy not currently verified
- rights chain unclear
- guaranteed profit or ROI claim
- unsafe title, tags, or description
- no A/B test plan
