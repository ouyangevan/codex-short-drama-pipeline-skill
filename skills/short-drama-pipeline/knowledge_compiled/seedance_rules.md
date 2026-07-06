# Seedance Rules

Use this compiled cache before searching a raw teaching database. Search raw or external teaching material only when this file lacks the needed rule, new teaching material was added, the user asks for relearning, or a rule conflict appears.

## Route Selection

- Text-to-video is for rough ideas, not continuity-critical short drama.
- Single-image I2V is for light motion from one frame; it drifts in long-form character/scene continuity.
- First/end-frame mode is for clear start and result states in one physical chain.
- Smart multi-frame mode is for larger transitions that need true intermediate physical states.
- Subject, multi-subject, omnireference, or multi-reference mode is preferred for locking character, scene, and prop identity across short-drama production.
- Agent mode can accelerate drafts, but it never replaces pipeline prompt review or QC.
- Use Fast for draft/preview/A-B testing. Use the higher-quality non-Fast route or another confirmed final route for final shots when cost and availability allow.
- For `fight_final`, use Fast for composition/action previsualization only. When a Seedance/Jimeng-style route is selected, prefer the higher-quality non-Fast/final route when the shot has three or more of: visible contact point, opponent reaction, prop state change, layered VFX such as dharma-body/suppression, non-locked camera, multiple reference assets, or final delivery intent.
- If Fast fails twice for unclear space, invisible contact, VFX hiding action, false opponent reaction, or prop drift, stop rewriting the same prompt and escalate route or split the shot.

## Seedance Combat Strategy

Seedance 2.0 full combat route:

- Use for complex battle, avatar/dharma-body, domain expansion, suppression field, magic collision, layered VFX, key contact, multi-reference control, and final delivery.
- Prefer first frame, key-pose/reference image, optional end frame, character reference, environment reference, weapon/prop reference, and optional VFX style reference.
- Keep one primary fight intent per shot even on the full route.
- Execution prompt may include spatial layout, character action chain, contact frame, VFX layer, environment feedback, and one camera motion.
- If the shot contains avatar, domain, or suppression, first create an establishing or `power_reveal_wide` shot, then create the contact/impact shot.
- Output asset requirements before render: character reference, environment reference, weapon/prop reference, first frame, optional end frame, and optional VFX style reference.

Seedance 2.0 Fast combat route:

- Use for short draft tests, one action, one contact, one result, and low-cost A/B.
- Compress to starting state, one main action chain, one clear contact/impact, and one result state.
- Do not put complex multi-stage battles, multi-character brawls, several spell systems, avatar plus domain plus weapon contact, or entire storyboard sequences into one Fast prompt.
- Full storyboard sheets are planning/review assets only. Before video generation, crop the selected panel or create a dedicated single-panel first/reference frame. Arrow guides, if used, must be made from the cropped panel duplicate, not from the full sheet.
- Prefer soft beat order over rigid `0-2s / 2-4s / 4-6s` timecodes unless the selected route specifically benefits from time labels.
- Fast prompts should read like one precise director instruction, not a complete director memo.
- If Fast fails from route overload, create a key-pose still and retry image-to-video, or escalate to the full route.

## Prompt Compiler Contract

For website/app use, the skill should compile render requests into structured artifacts, not only a prose prompt. A prompt pack for a selected Seedance/Jimeng-style route should output:

- `prompt_human_readable_zh`: Chinese review prompt for the user and director layer.
- `prompt_canonical_en`: English or provider-preferred canonical execution prompt when the route is more stable in English.
- `provider_execution_prompt`: compressed visible prompt actually sent to Seedance.
- `negative_constraints`: short critical constraints only.
- `api_params`: duration, ratio/aspect_ratio, resolution, seed, generate_audio, return_last_frame, model, route mode, and any provider-confirmed fields.
- `asset_bindings`: uploaded assets by role, order, source id, rights status, and phase.
- `qc_expectations`: key frames, action result, continuity, prop visibility, camera behavior, and failure blockers.
- For combat shots, include the Combat Pipeline structure: `style_route`, `fight_director`, `combat_beat`, `impact_system`, `vfx_power`, `camera_coverage`, `provider_route_strategy`, `asset_bindings`, `combat_qc_score`, and `qc_evidence`.

Do not put API parameters only in natural language. Duration, ratio, resolution, seed, audio, watermark, callback, and last-frame behavior must be represented as structured fields when the current provider supports them. Provider fields must be verified for the selected route; do not assume Cloudflare, fal, and Ark use the same names or capabilities.

## Render Service Contract

Codex/direct scripts are acceptable for prompt tests, but production website rendering should use a backend render service:

- create asynchronous tasks with an idempotency key from project, shot, prompt hash, model, seed, and asset ids
- retrieve/list/cancel tasks through provider APIs
- handle webhook callbacks or polling idempotently
- immediately archive `video_url` and `last_frame_url` into owned storage because provider URLs can expire
- record prompt hash, compiler version, skill version, model id, provider, seed, params, asset ids, task id, status, usage tokens, retry count, and QC result
- keep API keys server-side only

## First/End Frames

- The start frame must be the real pre-action state.
- The end frame must be the real result or aftermath state.
- Small natural transitions can use 5 seconds.
- Larger pose, background, style, camera-angle, or environment changes need 10 seconds, intermediate frames, or shot splitting.
- Do not force outdoor-to-indoor, day-to-night, major costume changes, or extreme pose jumps through one first/end-frame clip.
- In reference mode, images labeled as start/end are soft endpoint references unless the selected route explicitly supports first/end-frame locking.

## Reference Binding

- Map every upload by order and role before action text.
- State whether an image is a start frame, end frame, character reference, scene reference, prop reference, expression reference, storyboard/reference frame, or motion reference.
- Do not let one image carry conflicting roles.
- Keep one main scene reference per video prompt; split shots when location changes.
- Use video references only when legal or user-authorized, preferably 15 seconds or less, and name the exact purpose: action, camera movement, rhythm, pose path, or impact timing.
- Do not rely on direct upload of real-person face references unless the selected provider route explicitly permits the asset and the user has rights/consent. If a route rejects a real-person, celebrity, likeness, or identity-risk reference, return to character redesign or approved fictional/digital character assets instead of bypassing the rejection.

## Fast Prompt Compression

For Seedance 2.0 Fast, do not submit the full director reasoning layer as the model prompt. Use the director layer to design meaning, blocking, continuity, and audience comprehension, then compress it into visible, shootable instructions.

Fast prompts should prioritize:

1. opening frame relation: subject, scene, position, scale, facing direction
2. one core action chain
3. one primary camera movement
4. result state
5. no more than three critical guardrails

Convert abstract intent into visible evidence before submitting:

- "the viewer understands she is looking for a chance" -> "she stays low and stares at the exposed cable beside the mech's right leg"
- "tracking fails" -> "the gun is close but cannot tilt low enough"
- "the blue core means counterattack" -> "blue light from the core reflects on her glove and the wet floor"

For 5-6 second Fast clips, avoid three or more dense action phases plus complex camera, sound, prop, and narrative instructions in one prompt. If camera movement is the test target, put the camera instruction at the start and reduce action detail. If output fails, change one variable at a time: composition, then body action, then camera, then prop/result, then sound.

For fight tests, Fast prompts should prove only one variable per run: composition/spatial relation, body action/contact, camera behavior, prop/result state, or VFX attachment. Do not use Fast as proof that a complex final fight will work unchanged.

When references are available, separate control roles: start frame locks composition, character references lock identity/costume, scene references lock space/light, prop references lock scale/handling, and video references lock action or camera rhythm. If the route only exposes text or single-image input, prefer a shorter prompt plus a stronger start frame over a longer text prompt.

## Native Audio

- Enable native dialogue/Foley only on confirmed audio-capable routes unless the user disables it.
- Native audio may include approved dialogue and visible-source foreground Foley.
- Do not ask the video model for subtitles, UI text, watermarks, BGM, room tone, ambience beds, crowd chatter, or songs.

## Preflight

Before expensive generation check: route capacity, reference roles, frame phases, timing density, physical transition, character/scene consistency, style consistency, sound layer, Seedance Fast compression when applicable, and QC blockers.

