---
name: short-drama-pipeline
description: Use when the user explicitly asks to generate, produce, plan, revise, QC, or deliver an AI short-drama pipeline, project package, episode, assets-to-video workflow, prompt pack, clips, edit, or release pack.
---

# Short Drama Pipeline

## Purpose And Boundary

Run a repeatable AI short-drama production pipeline with source-backed rules, stable assets, professional direction, and hard delivery gates.

Use this skill only for explicit short-drama production work. For ambiguous requests, one-off prompts outside a short-drama project, high-tech premium videos, or external creative-agent platforms, read the relevant section of `references/boundaries.md`.

## Core Contract

1. Identify the current stage and whether the request is a lightweight `prompt_test_mode=true` experiment or normal production.
2. Follow the conservative source policy and stage reading route below before substantive work.
3. Reuse a valid stage cache and audit when upstream facts and rules have not changed.
4. Apply the three delivery gates. Never present failed or unverified output as usable.
5. Continue through the requested stage or finished-output workflow; stop only for a real blocker or required approval.

For normal production, read `references/operations.md` sections `Source Discipline`, `Delivery Gate Contract`, and `Hard Gates` once at project/session startup and reuse them while unchanged.

## Conservative Source Policy

The compiled cache is the first stable rule layer, not a quality downgrade.

- `prompt_test_mode=true`: read only the relevant `knowledge_compiled/` files by default. Read targeted reference sections when the cache is insufficient, the test is complex, a rule conflicts, or the result is being promoted to production.
- Normal production: read the relevant compiled files **and every stage-specific reference section listed in the routing table**. Do not omit a listed section. Read linked or adjacent sections too when the current artifact depends on them.
- Formal generation or delivery: also read the relevant blocker sections from `references/qc-gates.md`.
- Raw or external teaching-material search is allowed only on cache miss, conflict, new material, user-requested relearning, or missing rule coverage.

Never load an entire large reference merely because it is listed. Use heading search, then read from the required heading to the next same-level heading. Multiple required headings mean read all of those sections. Do not paste long rules into chat; apply them and cite their local path in the audit.

Compiled files:

- `knowledge_compiled/prompt_rules.md`: prompt readiness, still/video construction, prompt tests.
- `knowledge_compiled/camera_rules.md`: direction, camera, composition, light, pressure, spectacle.
- `knowledge_compiled/seedance_rules.md`: optional provider-profile rules for Seedance/Jimeng-style routes; use as a capability pattern only when the selected tool route matches.
- `knowledge_compiled/anime_fight_rules.md`: combat, anime battle, 3D donghua layout.
- `knowledge_compiled/common_failure_cases.md`: fast diagnosis, asset/prompt/video/edit failures.

Combat core files:

- `core/combat/fight_director_layer.md`
- `core/combat/combat_grammar.md`
- `core/combat/impact_system.md`
- `core/combat/power_escalation_system.md`
- `core/combat/vfx_power_system.md`
- `core/combat/combat_camera_coverage.md`
- `core/combat/combat_prompt_assembler.md`
- `core/combat/style_routes.md`
- `core/combat/combat_qc.md`

## Stage Reading Routes

This table defines the minimum production read. It is intentionally conservative: read more linked sections when dependencies apply, never fewer than listed.

### Boundary Or Skill Selection

- Reference: `references/boundaries.md` section `This Skill`, plus `Existing Skills` or `Ambiguous Requests` when relevant.

### Project Initialization, Idea, And Audience

- Compiled: relevant route files only.
- Workflow: `references/workflow.md` sections `0. Delivery Gates`, `1. Idea Intake`, `2. Audience Route`.
- Package: `references/project-package.md` sections `00_knowledge_read_audit.md`, `stage_cache/`, `00_idea.md`.
- Operations: `Knowledge Architecture`, `Source Discipline`, `Delivery Gate Contract`, `Tool And Model Confirmation Gate`, `Knowledge Use Gate`, `Knowledge Intake Audit`, `Stage Cache`, `Hard Gates`.

### Story Bible And Series Engine

- Compiled: `prompt_rules.md` when preparing downstream professional production.
- Workflow: `3. Story Bible`, `3B. Series Engine`.
- Package: `01_story_bible.md`, `01C_series_engine.md`.
- Prompt rules: `Narrative Engine And Audience Clarity Gate`.

### Professional Planning, Theme, Design, Coverage, And Performance

- Compiled: `prompt_rules.md`, `camera_rules.md`.
- Workflow: `3A. Professional Production Layer`, `3C. Theme And Mise-en-scene`.
- Package: `01A_director_treatment.md`, `01B_reference_board.md`, `01D_theme_and_mise_en_scene.md`, `03A_production_design_texture.md`, `03B_light_color_script.md`, `04A_coverage_plan.md`, `04B_blocking_and_performance.md`, `04D_lens_camera_language.md`, `04G_cinematography_bible.md`, `05A_editing_rhythm_map.md`, `05B_sound_director_layer.md`.
- Prompt rules: `Professional Production Gate`, `Narrative Engine And Audience Clarity Gate`, `Cinematography Bible Gate`, `Professional Direction Gate`.

### Script

- Workflow: `4. Script Package`; also reuse `3. Story Bible`, `3B. Series Engine`, and `3C. Theme And Mise-en-scene` when they constrain the episode.
- Package: `01_story_bible.md`, `01C_series_engine.md`, `01D_theme_and_mise_en_scene.md`.
- Prompt rules: `Narrative Engine And Audience Clarity Gate` when preparing a generation-bound script.

### Character Bible And Character Assets

- Compiled: `prompt_rules.md`, `common_failure_cases.md`.
- Workflow: `5. Character Bible`.
- Package: `02_character_bible.md`, `assets/character_packs/`.
- Prompt rules: `Prompt Delivery Gate`, `Still Image Prompt`.
- Formal preflight/QC: `references/qc-gates.md` section `Character Blockers`.

### Scene, Prop, Production Design, And Light Assets

- Compiled: `prompt_rules.md`, `camera_rules.md`, `common_failure_cases.md`.
- Workflow: `6. Scene Bible`, `6A. Prop And Evidence Ledger`.
- Package: `03_scene_bible.md`, `assets/scene_packs/`, `03C_prop_and_evidence_ledger.md`, `03A_production_design_texture.md`, `03B_light_color_script.md`.
- Prompt rules: `Narrative Engine And Audience Clarity Gate`, `Still Image Prompt`.
- Formal preflight/QC: `Scene Blockers`, `Physical Logic Blockers`.

### Storyboard, Frame Phases, Camera, And Cinematography

- Compiled: `prompt_rules.md`, `camera_rules.md`.
- Workflow: `7. Storyboard`, `7A. Cinematography Bible`.
- Package: `04C_frame_phase_plan.md`, `04_storyboard.md`, `04D_lens_camera_language.md`, `04G_cinematography_bible.md`.
- Prompt rules: `Narrative Engine And Audience Clarity Gate`, `Cinematography Bible Gate`, `Cinematic Intent Gate`, `Professional Direction Gate`.
- Formal preflight/QC: `Storyboard Blockers`, `Professional Direction Blockers`, `Cinematic Visual Blockers`, `Cinematography Bible Blockers`, `Physical Logic Blockers`.
- Storyboard asset rule: default to a full storyboard sheet for planning/review when generating multiple panels, then crop or create a dedicated single-panel frame for each video clip. Never upload the full multi-panel storyboard sheet as a video reference for one generation.

### Combat, Anime Battle, And 3D Donghua

- Trigger this Combat Pipeline for fights, duels, weapon clashes, hand-to-hand exchanges, magic collisions, avatar/dharma-body, suppression, domain expansion, burst attacks, reversals, dominance, 3D guoman battles, 2D high-dynamic combat, or live-action blockbuster-style fight coverage.
- Core combat: read `core/combat/fight_director_layer.md`, `core/combat/combat_grammar.md`, `core/combat/impact_system.md`, `core/combat/power_escalation_system.md`, `core/combat/vfx_power_system.md`, `core/combat/combat_camera_coverage.md`, `core/combat/combat_prompt_assembler.md`, `core/combat/style_routes.md`, and `core/combat/combat_qc.md`.
- Provider/schema: read `schemas/combat_prompt_compiler_output.schema.json` when the shot is app/backend-bound, and read provider notes only for the selected provider. If the selected route is Seedance/Jimeng-style, read `providers/seedance.md`. For multi-shot combat packages, also read `schemas/combat_prompt_compiler_sequence.schema.json`.
- Compiled: `anime_fight_rules.md`, `camera_rules.md`, `prompt_rules.md`, `common_failure_cases.md`; add `seedance_rules.md` only when the selected route is Seedance/Jimeng-style.
- Workflow: `7B. Anime Battle Direction Layer`, and `7B-2. 3D Donghua Action Layout Layer` when 3D layout applies.
- Package: `04E_anime_battle_direction.md`, and `04F_3d_donghua_action_layout.md` when applicable.
- Prompt rules: `Combat Dynamics Gate`, `Anime Battle Direction Gate`, and `3D Donghua Action Layout Gate` when applicable.
- Formal preflight/QC: `Combat Dynamics Blockers`, `Anime Battle Direction Blockers`, and `3D Donghua Action Layout Blockers` when applicable.
- Combat shots must not jump directly to an ordinary video prompt. First produce or update `combat_prompt_compiler_output.json` for a single shot, or `combat_prompt_compiler_sequence.json` for a multi-shot sequence, with fight director, combat beat, impact system, VFX power, camera coverage, provider route strategy, execution prompt, asset bindings, and combat QC score.

### Previs, Animatic, And Audience Comprehension

- Compiled: `prompt_rules.md`, `camera_rules.md`.
- Workflow: `7E. Previs And Animatic Plan`, `7F. Audience Comprehension Map`.
- Package: `04H_previs_animatic_plan.md`, `04I_audience_comprehension_map.md`.
- Prompt rules: `Narrative Engine And Audience Clarity Gate`, `Previs And Animatic Gate`.
- Formal preflight/QC: `Previs And Animatic Blockers`, plus `Storyboard Blockers` for audience-comprehension failures.

### Prompt Pack And Still Prompts

- Compiled: `prompt_rules.md`, `camera_rules.md`; add provider-profile rules such as `seedance_rules.md` only when the selected tool route matches those frame/reference/audio assumptions, and add `anime_fight_rules.md` for battles.
- Workflow: `8. Prompt Pack`.
- Package: `04C_frame_phase_plan.md`, `05_prompt_pack.md`.
- Prompt rules: `Prompt Delivery Gate`, `Professional Production Gate`, `Narrative Engine And Audience Clarity Gate`, `Cinematography Bible Gate`, `Previs And Animatic Gate`, `Cinematic Intent Gate`, `Professional Direction Gate`, `Still Image Prompt`; add battle sections when applicable.
- Formal preflight/QC: `Prompt Blockers`, `Physical Logic Blockers`, and relevant character/scene/battle blocker sections.

### Video Prompt, Tool Route, And Generation

- Compiled: `prompt_rules.md`, `camera_rules.md`, `common_failure_cases.md`; add `seedance_rules.md` or `anime_fight_rules.md` when applicable.
- Workflow: `8. Prompt Pack`, `9. Tool Route`.
- Package: `05_prompt_pack.md`, `06_generation_log.md`.
- Operations: `Tool And Model Confirmation Gate`, `Generation Interruption Policy`, `Hard Gates`.
- Prompt rules: `Video Prompt`, `Sound Taxonomy`, `Confirmed Native Dialogue/Foley Route`, and the matching duration template; add relevant professional/battle sections.
- Formal preflight/QC: `Prompt Blockers`, `Motion Reference And Timing Blockers`, `Physical Logic Blockers`, `Video Blockers`, and relevant asset/battle blockers.

### Editing, Audio, Final QC, And Release

- Compiled: `common_failure_cases.md`; add other compiled files when diagnosing their domain.
- Workflow: `10. QC and Release`.
- Package: `05A_editing_rhythm_map.md`, `05B_sound_director_layer.md`, `07_qc_report.md`, `08_release_pack.md`.
- Operations: `Delivery Gate Contract`, `Generation Interruption Policy`, `Hard Gates`.
- Prompt rules: `Sound Taxonomy`, `Confirmed Native Dialogue/Foley Route` when generated audio is involved.
- QC: `Audio/Edit Blockers`, `Final Render Blockers`, `Release Blockers`, plus every media-specific blocker section relevant to the deliverable.

### Prompt Testing

- Compiled: only files relevant to the test.
- Operations: `Prompt Testing Mode`.
- Targeted prompt/QC reference sections are required only when compiled rules are insufficient, the test is complex, or the result is promoted to production.

### Knowledge Cache Miss, Conflict, Or Re-audit

- Operations: `Knowledge Architecture`, `Source Discipline`, `Teaching Material Knowledge Base`, `Knowledge Use Gate`, `Knowledge Intake Audit`.
- Package: `00_knowledge_read_audit.md`.

## Delivery Gate Contract

No substantive production output is usable unless every applicable gate passes:

- `knowledge_gate`: PASS only when the current stage audit records required compiled files, every routed reference section opened, valid stage-cache reuse, rules applied, and a passing pre-output compliance check. Record raw searches only when escalation was required.
- `asset_gate`: PASS, FAIL, or N/A. Serious character-consistent video requires complete core character packs; serious moving-camera/reverse-shot video requires complete core scene packs.
- `qc_gate`: PASS, FAIL, QC_UNVERIFIED, or N/A. Generated images, clips, edits, and release files require actual inspection against the relevant `qc-gates.md` sections.
- `allowed_output`: `deliverable` only when all applicable gates pass; otherwise `blocked_report_only`.

If `knowledge_gate` fails, do not create the production artifact. If `asset_gate` fails, do not call serious video generation. If `qc_gate` fails or is unverified, do not present the output as usable.

For user-facing stage deliveries:

```text
Gate Status:
- knowledge_gate: PASS/FAIL
- asset_gate: PASS/FAIL/N/A
- qc_gate: PASS/FAIL/QC_UNVERIFIED/N/A
- allowed_output: deliverable|blocked_report_only
```

When a project package exists and the current project configures a delivery validator, run it before user-facing delivery. A failed validator overrides agent judgment. If no executable validator exists, record `executable_gate: N/A`.

## Audit And Cache Rules

- Update `00_knowledge_read_audit.md` at project initialization, at a new stage, on cache miss/conflict, when new teaching material exists, or when the user requests relearning.
- Do not refresh a full audit for every shot, wording change, or retry inside an already audited stage.
- Every production stage has a stage-start read and a pre-output compliance check.
- Reuse valid `stage_cache/` artifacts when upstream story, character, scene, style, route, and QC facts are unchanged.
- Never claim a full database re-audit unless the target corpus was processed in chunks and an external report was saved.

## Prompt Test Exception

`prompt_test_mode=true` is draft-only. It may skip raw teaching rereads, project-package creation, bible regeneration, full audit refresh, and the delivery validator. It never bypasses production Asset Gate or QC Gate. Promotion to production requires the normal routed reads and gates.

## Reference Ownership

- `references/workflow.md`: complete stage workflow and stage requirements.
- `references/project-package.md`: complete project file and asset templates.
- `references/prompt-rules.md`: complete professional still/video prompt specifications and templates.
- `references/qc-gates.md`: complete media, prompt, edit, final-render, and release blockers.
- `references/operations.md`: complete knowledge-source policy, tool/model confirmation, audits, cache, prompt-test mode, interruption policy, and hard gates.
- `references/boundaries.md`: skill selection and ambiguous-request boundaries.
- `core/combat/`: Fight Director System modules for fictional 3D guoman, 2D high-impact animation, and live-action-style combat.
- `providers/`: provider-specific strategy notes.
- `schemas/`: compiler schemas for website/backend integration.
- Host-local validators, private research corpora, and provider credentials are optional local overlays. Do not put personal paths, private corpora, or raw secrets in the public skill.

Detailed rules live in these references. Do not recreate or shorten their requirements from memory.

## Optional Executable Gate

For normal short-drama production, model-authored gate claims are not sufficient.
Prefer an executable validator or host hook when the current project provides one, but do not assume a private local script exists in the public distribution.

1. If a project-specific validator or gate hook is configured, run it before production work, before reference-bound generation, and before user-facing delivery.
2. If no executable validator exists, record `executable_gate: N/A` and rely on the required `knowledge_gate`, `asset_gate`, and `qc_gate` records.
3. Read every routed file and targeted section directly. Search results and unsupported claims in chat do not count as opened evidence.
4. Before reference-bound generation, record every upload in order with role, path or asset id, source or rights status, and generation purpose.
5. Immediately before one formal generation call, complete a preflight record that checks routed reads, asset bindings, provider capability, and blocker sections.
6. Record actual media inspection in the QC report. Never describe a failed, blocked, or uninspected artifact as usable.
