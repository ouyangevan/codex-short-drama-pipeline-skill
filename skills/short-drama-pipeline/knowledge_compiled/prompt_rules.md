# Prompt Rules Cache

Use this compiled cache for prompt construction and optimization before searching the teaching database.

## Prompt Readiness

Generation-ready prompts require a passing knowledge gate, passing or non-applicable asset gate, and required professional artifacts.

For website/app integration, prompt packs must be compiler outputs, not only a text prompt. Include human-readable director text, canonical execution prompt, provider execution prompt, negative constraints, API params, asset bindings, and QC expectations.

For final-level fight/action generation, use the Combat Pipeline compiler mode. The output must include `style_route`, `fight_director`, `combat_beat`, `impact_system`, `vfx_power`, `camera_coverage`, `provider_route_strategy`, `negative_constraints`, `asset_bindings`, `qc_expectations`, `combat_qc_score`, and `qc_evidence` before any prose prompt.

For professional-level prompt packs, inherit:

- story bible and series engine
- director treatment and reference board
- theme and mise-en-scene
- character bible and scene bible
- prop/evidence ledger
- coverage, blocking, performance, actor rehearsal
- lens/camera language and `04G_cinematography_bible.md`
- light/color, production design, editing rhythm, sound director
- frame phase plan
- `04H_previs_animatic_plan.md`
- `04I_audience_comprehension_map.md`
- `04E` and `04F` when anime/3D battle applies

## Still Prompts

Still prompt formula: style + subject + character appearance/clothes/action + scene/background + shot/composition + light + quality.

- Character assets need four-view, expression, marker/detail, and close-up references.
- Scene assets need 720-degree/multi-angle references, key camera positions, state variations, and prop close-ups.
- Prop assets need independent prop image plus character-bound scale/use references when repeated.
- Starting frame, storyboard/reference frame, and ending frame are distinct causal phases unless the shot is intentionally static.
- A full multi-panel storyboard grid is a planning/review artifact, not a video reference for one generation. For video generation, use a cropped single-panel or dedicated frame reference per generated clip. If no upscale/repair route is configured, do not block generation on upscale; use the cropped panel after basic QC.

## Video Prompts

Video prompt formula: named character + location + current state + action change + expression change + camera movement + dialogue/open-mouth state + foreground Foley + continuity state.

- One shot equals one performable action or emotion turn.
- Rapid repeated strikes can be one performable combo beat when they share one tactical objective, spatial route, camera design, and result. Do not split continuous slashes or punches merely because several hits occur.
- Fight/action prompts must inherit an action-meaning and spatial-continuity pass before wording: each character needs start/end position, facing direction, screen direction, body state, tactical intention, enemy counter-action, prop state, viewer information delta, and carry-forward state for the next shot.
- `fight_final` prompts must be compiled from three layers: director layer for story meaning, action graph layer for physical/contact/VFX logic, and execution layer for the short provider prompt and structured API params. Do not send the full director layer as the execution prompt.
- Split instead of compressing when a fight shot has more than one tactical objective, more than two visible contact events, more than one major camera behavior, or more than one major VFX state shift.
- Do not write a character motion only as "prepares", "slides", "dodges", "connects", "crawls", "stands", or "breathes". State why the character does it, what the opponent does in response, what the viewer understands, and how the power relation changes.
- Split dense action, multi-scene movement, or competing dialogue/action.
- For a finished sequence, generate multiple storyboard panels as separate clips and stitch/edit them together. Do not upload a full storyboard grid or ask one video generation to perform the whole grid.
- For fast/low-control video routes, keep the submitted execution prompt shorter than the internal director layer. Compress to visible, shootable information: opening frame relation, one core action chain, one primary camera movement, result state, and no more than three critical guardrails.
- Do not submit abstract director/audience wording directly to low-control routes. Convert it to visible evidence: gaze, posture, distance, object position, gun angle, light reflection, body mechanics, and result state.
- 5 seconds usually carries 2-3 clear beats; 8-10 seconds carries 4-6 beats.
- Do not use pronoun-only references.
- Do not ask for subtitles, UI, watermarks, BGM, ambience beds, or crowd chatter.
- Include sound only when it is approved dialogue or visible/source-clear foreground Foley.
- Parameters such as duration, ratio/aspect ratio, resolution, seed, audio, return_last_frame, callback, and provider/model route belong in `api_params` when supported. Do not rely on prompt prose alone for these controls.

Fight prompt repair must diagnose one primary failure before rewriting. Use this order: action overload, missing contact visibility, unclear spatial axis, reaction not bound to contact, VFX occluding action, camera competing with action, missing prop binding, style conflict, weak model route. A repair output must say what to keep, what to remove, the revised shot graph, revised execution prompt, and revised API params.

## Prompt Test Mode

When `prompt_test_mode=true`, outputs are draft-only prompt tests. They may optimize wording, compare route choices, or analyze selected-provider behavior, but they are not production-ready unless revalidated in normal mode.

