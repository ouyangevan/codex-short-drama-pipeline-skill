# Operations And Knowledge Policy

Read only the section required by the current stage. Do not load this entire file unless the user explicitly requests a full policy audit.

## Knowledge Architecture

This skill separates long-lived production knowledge from per-project runtime work.

Static Knowledge:

- provider-route patterns, first/end-frame logic, multi-reference binding, native-audio limits, and route-capability checks
- camera, lens, composition, light, blocking, pressure/tension, and professional direction rules
- combat, anime battle, and 3D donghua action-layout rules
- character/scene/prop consistency rules
- prompt best practices and common failure cases
- approved teaching-material conclusions that have already been compiled

Dynamic Tasks:

- the current idea, audience route, script, shot, prompt, generated result, failure analysis, QC result, and release decision
- tool route capability/pricing/commercial terms that must be verified at execution time
- project-specific story bible, character bible, scene bible, cinematography bible, prompt pack, generation log, edit, and release package

Default source order:

1. Read the relevant file in `knowledge_compiled/`.
2. Read the relevant skill reference file in `references/`.
3. Reuse valid project `stage_cache/` artifacts when the upstream facts have not materially changed.
4. Search raw or external teaching material only on cache miss, new teaching material, user-requested relearning, rule conflict, or missing rule coverage.

Compiled knowledge files:

- `knowledge_compiled/seedance_rules.md` as an optional provider-profile example for Seedance/Jimeng-style routes, not as a required default for every user
- `knowledge_compiled/camera_rules.md`
- `knowledge_compiled/anime_fight_rules.md`
- `knowledge_compiled/prompt_rules.md`
- `knowledge_compiled/common_failure_cases.md`

Do not treat the cache as a quality downgrade. The cache is the approved stable rule layer. Teaching-database search is the escalation path, not the default runtime path.

## Source Discipline

Only use approved completed teaching-material conclusions. Do not use unfinished videos, unread documents, inaccessible links, unverified platform claims, or assumed tool capabilities as rules.

Business-sensitive facts are live facts. Tool pricing, model capability, platform policies, monetization rules, and commercial license terms must be rechecked at execution time.

Strictly follow the bundled compiled rules and any project-approved local teaching-material conclusions for production decisions. Cache-backed and source-backed rules override generic model knowledge, personal habit, and chat-memory assumptions. If the bundled cache, local source corpus, and this skill conflict, stop, cite the conflict, and ask the user before proceeding.

Before any substantive production action, consult the relevant compiled knowledge file, skill reference, and existing project stage cache for that stage. Record the evidence in `00_knowledge_read_audit.md` at project initialization and when a new stage starts. Substantive production actions include script writing, story bible changes, character design, scene design, storyboard, prompt pack writing, video generation, editing, QC, and release packaging. Do not act only from chat memory. Search the raw teaching database only when the compiled cache misses or conflicts, new teaching material exists, the user requests relearning, or the needed rule is not covered.

When the user asks for a finished short-drama output, do not stop at a workflow description. After the action-specific knowledge read, proceed through project package creation, generation, editing, QC, and delivery using the tools the user has available and approves for the run. Stop only for real blockers such as missing assets, account/credit limits, inaccessible tools, model rejection, safety/compliance blockers, or user-required approval gates.

## Delivery Gate Contract

No substantive output may be delivered as usable unless all required gates are visible and passing. This is a hard contract, not a reminder.

Every stage artifact, generated asset batch, prompt pack, video clip batch, edit, QC conclusion, or release package must include or point to a current gate record with:

- `knowledge_gate`: `PASS` only if `00_knowledge_read_audit.md` names the stage, the compiled knowledge cache files used, the relevant skill references opened, valid stage-cache artifacts reused if applicable, source-backed rules applied, and `pre_output_compliance_check`. If the compiled cache misses, the audit must also record `rg` query terms, opened teaching-database source files, and the new rules copied back into the current stage constraints.
- `asset_gate`: `PASS`, `FAIL`, or `N/A`. It can be `PASS` for character assets only when every core character has four-view, expression, marker/detail, and close-up references. It can be `PASS` for scene assets only when every core scene has 720-degree/multi-angle spatial references, key camera positions, state variations, and prop close-ups.
- `qc_gate`: `PASS`, `FAIL`, or `N/A`. It can be `PASS` only after the artifact or generated output has been inspected against `references/qc-gates.md`; uninspected output is `QC_UNVERIFIED`, not pass.
- `allowed_output`: `deliverable` or `blocked_report_only`.

If `knowledge_gate` is missing or fails, do not write scripts, assets, prompts, generation calls, edits, QC conclusions, or release files. Output only `BLOCKED: knowledge gate failed`, then list the missing cache reads, source reads, cache-miss searches, or stage-cache checks.

If `asset_gate` fails, do not call video generation and do not describe a single portrait or mood image as production-ready. Label it `draft_only_not_generation_ready`, then create or request the missing four-view/expression/marker/close-up or 720-degree/multi-angle scene pack.

If `qc_gate` fails or is `QC_UNVERIFIED`, do not send the output as a result, finished asset, usable reference, or final clip. Output only a failed-QC report with the problem, violated rule, fix route, and retry plan. A failed image or clip may be referenced only as failed evidence, never as the deliverable.

For user-facing stage deliveries, include a compact gate block before the artifact summary:

```text
Gate Status:
- knowledge_gate: PASS/FAIL
- asset_gate: PASS/FAIL/N/A
- qc_gate: PASS/FAIL/QC_UNVERIFIED/N/A
- allowed_output: deliverable|blocked_report_only
```

When a project package folder exists, run the local validator configured for the current host before any user-facing deliverable. If no executable validator is configured, record `executable_gate: N/A` and rely on the documented gate evidence.

If the validator prints `FAIL: blocked_report_only`, do not deliver the artifact as usable. Report the failed checks and fix the package first.

## Tool And Model Confirmation Gate

Before starting any new short-drama production run, ask the user which tools and models are available and approved for this run. Do this before writing generation-ready prompts, creating assets, calling image/video/audio tools, or committing to a cost/resolution route.

Ask for or confirm at least:

- image generation tool and model, or confirm that image generation is unavailable and the run must stay as a package/prompt dry run
- video generation tool and model, or confirm that video generation is unavailable and the run must stop before render calls
- audio/voice route and model, including which selected video routes support native dialogue/Foley audio. Enable native audio/sound effects on selected audio-capable video models unless the user explicitly disables it.
- editing/rendering route
- resolution and cost mode, such as 480p draft, 720p test, 720p final, or 1080p final
- whether to use a project model-route config or only tools named in the chat

A model-route config is optional and host-specific. Use the current project's documented config path when one exists; otherwise ask the user to confirm tools and models before generation.

If the user has already specified the route in the current request, restate it and ask for confirmation before generation. If the shared config exists and contains enabled defaults, show the selected route and ask for confirmation. If the config is missing, incomplete, or conflicts with the user's request, ask the user before proceeding.

Never write raw API keys into this skill, teaching-material files, project packages, prompt packs, or public logs. Store only provider names, model names, base URLs, capability notes, and environment-variable names. API keys must live in environment variables or another approved local secret store.

For all-project availability, prefer stable environment-variable names chosen by the project. A route config may point to names such as:

- `SHORTDRAMA_IMAGE_PROVIDER`, `SHORTDRAMA_IMAGE_MODEL`, `SHORTDRAMA_IMAGE_BASE_URL`, `SHORTDRAMA_IMAGE_KEY`
- `SHORTDRAMA_VIDEO_PROVIDER`, `SHORTDRAMA_VIDEO_MODEL`, `SHORTDRAMA_VIDEO_BASE_URL`, `SHORTDRAMA_VIDEO_KEY`
- `SHORTDRAMA_AUDIO_PROVIDER`, `SHORTDRAMA_AUDIO_MODEL`, `SHORTDRAMA_AUDIO_BASE_URL`, `SHORTDRAMA_AUDIO_KEY`

Provider credentials should live in the approved local secret store for the current host. Do not ask the user to re-enter keys unless the variables are missing or a route test proves the key is invalid.

The route config may name any provider the user has access to, including direct APIs, hosted model gateways, web tools, local tools, or manual upload workflows. Do not assume Vidu, Kling, Seedance, GPT Image, Seedream, Runway, Pika, Luma, Midjourney, ComfyUI, or any other tool is present unless the user or config confirms it.

When a new chat starts a short-drama project, first open the configured model route file for the current host when one exists, then check whether the required credentials or manual-access route exist. The check should report only route names and variable presence, never raw key values.

Do not ask the user to paste raw keys into chat unless there is no safer option. Prefer guiding the user to set the environment variables locally.

No image model is a built-in default. Use the best available user-approved image route for photos, still frames, starting frames, storyboard frames, character assets, scene assets, and prop assets. If no image route exists, produce prompts and package artifacts only, mark asset generation blocked, and do not claim the asset gate passes. Generated image assets still need the normal knowledge gate, role labels, character/scene/prop purpose labels, and QC before they can be used downstream.

Before generating or using any short-drama image asset, explicitly decide and record whether it is a starting frame, ending frame, storyboard/reference image, character reference, scene reference, or prop reference. Do this before writing the prompt or calling any generator; never let a dramatic storyboard/result image silently become the starting frame for a cause-and-effect video action.

Use confirmed video routes that support the required reference capacity. The route can be a direct API, web UI, local workflow, hosted gateway, or manual upload flow. Do not force a shot into a weaker route: if the available model cannot support the required character, scene, prop, first/end-frame, video-reference, or audio-reference controls, revise the shot, reduce control requirements with user approval, or stop at a blocked report.

## Teaching Material Knowledge Base

When a project has local teaching-material summaries, consult them before making workflow decisions. If no local corpus is configured, use the bundled `knowledge_compiled/` files and mark raw-source escalation as unavailable unless the user supplies sources.

Database scale recorded during Stage 1:

- 340 inventoried files, about 45.62 GB total.
- 193 videos, about 81.87 hours total.
- 148 videos marked `transcribed_complete`.
- 45 videos marked `visual_review_complete_limited_use`.
- Supporting materials include text files, spreadsheets, PDF, DOCX, ZIP archives, images, extracted text, transcripts, visual-review notes, and test project assets.

## Knowledge Use Gate

A new chat must not treat this skill as only a checklist. The compiled knowledge cache is the default source of stable production rules. The raw teaching-material database is the escalation source for cache misses, conflicts, new teaching material, and user-requested relearning.

Before creating a new short-drama project package or finished short-drama output, complete a minimum cache knowledge pass and write it into `00_knowledge_read_audit.md`:

- Read the relevant files in `knowledge_compiled/` for the current task.
- Read the stage-relevant skill references in `references/`.
- Record `knowledge_cache_status`: `hit`, `partial_hit`, `miss`, or `conflict`.
- Record the stable rules applied, the cache file path, and the stage they constrain.
- Search the raw teaching database only when `knowledge_cache_status` is `partial_hit`, `miss`, or `conflict`, or when the user requests relearning or new teaching material has been added.
- If raw search is required, record `rg` queries, matched files, opened sections or transcript chunks, source status, and the rules copied into the project audit.

Do not summarize or generate from "database knowledge" unless the audit proves which cache file or raw source section was used. A fast startup pass that only opens this `SKILL.md` is not enough to write scripts, prompts, storyboard rules, generation settings, QC conclusions, or release packages.

Before generating each different stage, perform a stage-start cache lookup. Required stages include idea intake, story bible, series engine, director treatment/reference board, theme/mise-en-scene, script, character bible, character assets, scene bible, prop/evidence ledger, production design, light/color script, scene assets, coverage plan, blocking/performance plan, actor rehearsal, lens/camera language, storyboard, frame phase plan, anime battle direction when applicable, 3D donghua action layout when applicable, audience comprehension map, prompt pack, generation route, video generation, editing rhythm map, sound director layer, editing/audio, QC, and release pack. If the cache hits and no rule conflict exists, do not search raw teaching material. If the cache misses and a local or external corpus is available, search it with `rg`, open relevant sections or transcript chunks, and record the new source-backed rules in the audit.

Every stage has a mandatory two-pass knowledge gate:

1. Stage-start read: before planning, writing, or changing the stage, open the relevant compiled cache and skill-reference sections, then record the rules that will constrain the stage. Search raw teaching material only on cache miss, conflict, new material, or user-requested relearning.
2. Pre-output compliance check: immediately before emitting the stage artifact, final prompt, generation call, edit decision, QC conclusion, or release package, compare the current artifact or prompt against the already loaded compiled rules, stage-cache artifacts, asset gates, and QC blockers.

Record the second pass as `pre_output_compliance_check` in `00_knowledge_read_audit.md`. It must list the cache files checked, stage-cache artifacts reused, checklist items checked, pass/fail result, revisions made, and final approval to generate or deliver. If raw database search was needed, also list `rg` queries and opened source files. If any required rule fails, revise the artifact or prompt first and repeat the check. Do not generate, call tools, edit, deliver, or mark a stage complete on a failing or missing `pre_output_compliance_check`.

If the user explicitly asks for a full database re-audit, process the corpus in chunks and save an external report before production. Do not try to load the whole database into chat context at once.

New-chat startup rule:

1. If the user says to use this流水线短剧 skill, open `SKILL.md`, then read the relevant compiled cache files before searching raw teaching materials.
2. If the task involves a provider with first/end frames, multi-reference generation, native audio, prompt packs, or anime/3D battles, open the matching `knowledge_compiled/` files. Open `seedance_rules.md` only when the selected route is Seedance/Jimeng-style or the user wants to compare against that provider profile.
3. Use raw or external teaching-material search only on cache miss, conflict, new material, user-requested relearning, or a missing rule.
4. If creating a project package, load the relevant cache and workflow references first, then consult raw teaching notes only when the cache cannot answer the current stage.
5. Do not rely on chat memory alone. Treat the compiled cache plus source-backed audit as the durable knowledge base.
6. Keep the boundary clear: this is the流水线短剧 pipeline, not the `high-tech-short-video` premium single-video workflow.

Context budget rule:

- Never load `combined_extracted_text.md`, `inventory.json`, the full `video_transcripts\` folder, or the full `zip_extracted\` folder into context at once.
- Do not paste entire teaching files into the answer. Summarize the relevant sections and cite the local file path.
- For broad tasks, keep a small working summary in the project package and refresh it stage by stage.
- For full re-audits, process the knowledge base in chunks and write an external report file instead of carrying everything in chat context.

## Knowledge Intake Audit

Do not claim to have fully read or mastered the entire local database during a short startup pass. The database is too large for a normal chat turn. A quick startup read can only be described as reading the required skill files, primary summaries, and relevant searched sections.

Refresh the audit only at project initialization, when a new stage starts, when the knowledge cache misses or conflicts, when new teaching material is added, or when the user requests relearning. Do not run a full audit for every shot, prompt wording change, or retry inside an already audited stage.

For a new audited stage, record:

- action about to be taken: script, character, scene, storyboard, prompt, generation, edit, QC, or release
- `knowledge_cache_status`: `hit`, `partial_hit`, `miss`, or `conflict`
- compiled knowledge files opened
- skill reference files opened for that action
- valid stage-cache artifacts reused, if any
- knowledge-base files or searched sections opened only when cache miss/conflict requires raw search
- `rg` query terms used only when raw teaching search is required
- rules from the sources that will constrain the action

If the audit lacks the stage-start cache evidence, stop and read the relevant cache/reference files before producing the next artifact. If the cache misses and no raw search is recorded, stop and search the relevant teaching sources.

Before generating a project package, create or update a knowledge intake audit. The audit must list:

- required routed sections read: `SKILL.md`, the relevant compiled files, and every reference heading required by the current stage route in `SKILL.md`; do not full-read all large references by default
- compiled knowledge files read from `knowledge_compiled/`
- primary raw knowledge files read only on cache miss, conflict, new material, or user-requested relearning
- topic searches performed with `rg`, including query terms and matched source files, only when raw teaching search is required
- transcript chunks or original-material sections opened for the current stage only when raw teaching search is required
- source status used for decisions: `approved_summary`, `transcribed_complete`, `visual_review_limited`, `unverified`, or `not_read`
- rules applied to the current output
- `pre_output_compliance_check` for each stage: cache files checked, reused stage-cache artifacts, prompt/artifact checklist, pass/fail result, revisions made, and approval to generate or deliver
- unknowns, missing access, outdated tool claims, or facts needing live verification

If the audit is missing, incomplete, or only says "read completely" without cache/source evidence, the knowledge intake is not complete and the agent must not proceed as if it has mastered the database.

When answering the user, be precise about scope:

- Say "I read the required startup files and relevant knowledge-base sections" when that is what happened.
- Say "I performed a full re-audit" only after chunked processing of the full target corpus and an external report file.
- Never use unread transcripts, unreviewed visual material, inaccessible links, or outdated tool claims as workflow rules.

## Stage Cache

Every project package may include `stage_cache/` for reusable stage outputs:

- `stage_cache/story_bible.md`
- `stage_cache/character_bible.md`
- `stage_cache/scene_bible.md`
- `stage_cache/cinematography_bible.md`

If one of these artifacts already exists and there is no material upstream change, reuse it instead of regenerating it.

Material upstream changes include:

- story premise, protagonist goal, conflict, episode structure, theme, or reversal changes
- character identity, age, role, face/body DNA, costume, status, relationship, or performance route changes
- scene location, spatial anchors, time of day, light logic, material texture, prop layout, or continuity-state changes
- visual style, aspect ratio, target platform, camera grammar, generation model, or route-capability changes
- a failed QC result proving the cached artifact caused a downstream error

When reusing a cached stage, record `stage_cache_hit` in `00_knowledge_read_audit.md` with file path, dependency check, and reuse decision. If a material upstream change exists, record `stage_cache_invalidated` and regenerate the stage.

## Prompt Testing Mode

`prompt_test_mode=true` is a lightweight testing mode for high-frequency prompt experiments.

Allowed:

- prompt generation
- prompt optimization
- selected-provider route analysis
- first/end-frame versus multi-reference reasoning
- failure analysis of test prompts or test clips

Skipped:

- raw teaching-database rereads
- new project package creation
- bible regeneration
- full audit refresh
- delivery validator

Hard limits:

- Output is `draft_only_prompt_test`, not production-ready.
- Do not call it a usable prompt pack, generation-ready package, or deliverable.
- Do not bypass Asset Gate or QC Gate for production.
- To promote a prompt-test result into production, return to normal mode, load the required compiled cache and stage-cache artifacts, run the appropriate gates, and validate the package when a project folder exists.

## Generation Interruption Policy

Route generation blocks by media type:

- Still images for photos, storyboard frames, character assets, scene assets, and prop assets are retryable. If image generation is blocked, fails, or returns an unusable image, retry with a compliant prompt while preserving the approved story beat, character DNA, scene anchors, and asset purpose. Record the original problem, changed prompt/visual handling, retry count, output file, and QC result in the generation log. After the batch or shot is completed, explain what went wrong and what changed.
- Stop immediately only for video generation blocks, real-person/celebrity/IP identity-risk blocks, or any still-image retry that would require changing approved story causality, character identity, or scene facts. Return to the nearest upstream stage and get user confirmation before continuing.
- A rejected still image is not a substitute for an approved frame. Only a generated image that passes QC can be used as a starting frame, ending frame, character reference, expression reference, scene spatial reference, prop reference, or storyboard reference.

## Hard Gates

- No unlicensed story, music, face, voice, character, or recognizable IP.
- No celebrity likeness or voice imitation without authorization.
- No platform bypass, piracy, or hidden-source downloading workflow.
- No watermark-removal workflow as a commercial production step. If a teaching link mentions watermark removal, record it as an unapproved source note and do not use it for release assets.
- No unlicensed IP, fan-content, celebrity, existing character, or recognizable third-party franchise material from traffic/self-media lessons as overseas commercial short-drama material. Learn only the audience, hook, account, and testing principles.
- No bypassing platform real-person, likeness, or identity-risk detection. If a model rejects a reference as a real person or celebrity-like asset, return to the character asset stage and redesign the character as an original fictional character.
- No partial style workaround after model rejection. If the selected video route rejects one reference, do not change only that asset or shot to 2.5D, anime, pencil, sketch, oil-painting, or another style to force acceptance while the project remains realistic/live-action/CG. Repair in the approved project style, or ask the user to approve a full project style migration and regenerate the affected character, scene, prop, storyboard, and prompt assets.
- No guaranteed profit or ROI claim.
- No text-to-video as the default production path when character and scene consistency matter.
- No single glamour character image as the only character reference. Core characters need four-view and expression references before serious video generation.
- No single mood scene image as the only scene reference. Core scenes need 720-degree/multi-angle spatial references before serious camera movement or reverse shots.
- No treating "model test", "performance test", "benchmark", "low-cost test", or "first run" as permission to skip character and scene asset gates when the output will be used for short-drama video generation. A simplified reference set is allowed only when the user explicitly asks for a text-only, one-image, or rough non-production test, and the prompt pack/generation log must label it as invalid for serious continuity evaluation.
- No video model subtitles, UI, watermarks, or BGM generation. Add text in post. For audio-capable video routes, do not disable native dialogue/Foley by default; generated audio must be limited to approved dialogue and visible/source-clear foreground sound effects.
- For any confirmed native dialogue/Foley route, keep audio foreground-only. This applies to any selected video model that supports generated sound. Allowed native audio: approved character dialogue in the target language plus visible/source-clear story sounds such as glass shattering, a door being forced open, pen spinning or rolling, cup impact, chair scrape, footsteps, cloth movement, and breath. Forbidden native audio: banquet-hall chatter, indistinct party conversation, crowd murmur, room tone, ambient background beds, music, BGM, songs, lyrics, or soundtrack beds. Background music and broad atmosphere belong in post-production, not in generated clips.
- Do not use a one-image/text-only route as the default production route when the shot needs multi-reference character, scene, prop, first/end-frame, video-reference, or audio-reference control.
- No pronoun-only video prompts. Name the character or repeat character DNA.
- No incomplete research source as evidence.
- No frozen-tail padding as a normal edit solution. If a voiced shot outlasts usable video, first shorten/rewrite the line, split it over a reaction shot, regenerate a longer clip, or apply only subtle retiming. Frozen tails are a QC failure unless explicitly approved for a deliberate freeze-frame effect.
- No system TTS voice as the final overseas-release voice. Local Microsoft/SAPI voices are placeholders only. Published English cuts should use expressive TTS or recorded voice with controllable emotion, pacing, pauses, and intonation, then lock captions to real audio timing.
- No top-tier 3D 国漫 / 3D anime-style battle prompt without `04F_3d_donghua_action_layout.md` when the requested quality depends on 3D layout, animation mechanics, contact/IK, FX-light-compositing, battle asset states, and action readability.
