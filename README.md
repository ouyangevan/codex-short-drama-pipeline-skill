# Short Drama Pipeline Skill

Provider-agnostic Codex skill for planning, packaging, prompting, validating, and releasing AI short-drama projects.

This skill is for creators and teams who already have access to one or more image, video, audio, editing, API, local, or manual-upload tools and want a repeatable production workflow around them. Its value is the workflow, capability matching, asset discipline, prompt compiler structure, and delivery gates, not a fixed provider stack.

## What It Does

- Turns an idea into a structured short-drama project package.
- Builds story, character, scene, prop, storyboard, prompt, generation-log, QC, and release artifacts.
- Routes work by capability: image assets, video drafts, final video, audio, editing, manual upload, or dry-run package.
- Provides hard gates for knowledge use, asset readiness, media QC, and delivery status.
- Includes combat and anime battle prompt compiler layers for readable screen action.
- Validates single-shot and multi-shot combat compiler artifacts with JSON schemas.

## What It Does Not Do

- It does not require Seedance, Kling, Vidu, GPT Image, Seedream, Runway, Pika, Luma, Midjourney, ComfyUI, or any other fixed provider.
- It does not include private account credentials, API keys, host-local validators, or personal workflow overlays.
- It does not promise one-click generation. Missing tools should produce a dry-run package and a blocked gate, not fake completion.
- It does not replace final human review for story taste, commercial rights, or platform compliance.

## Install

Copy `skills/short-drama-pipeline` into your Codex skills directory, then start a new Codex session.

```powershell
Copy-Item -Recurse .\skills\short-drama-pipeline "$env:USERPROFILE\.codex\skills\short-drama-pipeline"
```

## Quick Start

After installation, start with a request like:

```text
Use short-drama-pipeline to turn this idea into a project package and prompt pack.
My available tools are: image model X, video model Y, audio route Z.
If a tool is missing, produce a dry-run package and mark the blocked gate.
```

The agent should first confirm available tools, then map them to route capabilities:

- image assets: character sheets, scene packs, props, still frames
- video generation: text-only, image-to-video, first/end frames, multi-reference, video-reference, native audio
- audio/editing: voice, Foley, music, captions, final render
- fallback: package-only or prompt-only dry run when generation tools are unavailable

## Example Requests

```text
Use short-drama-pipeline to build a 3-episode vertical revenge drama package.
I only have an image model and a web video tool, so stop before final media generation if gates fail.
```

```text
Use short-drama-pipeline to compile this fight scene into combat_prompt_compiler_output.json.
My final video route supports first frame, end frame, character reference, and prop reference.
```

```text
Use short-drama-pipeline in prompt_test_mode=true to compare two video prompt drafts.
Do not create a full project package yet.
```

## Quality Gates

Every production artifact should report:

```text
Gate Status:
- knowledge_gate: PASS/FAIL
- asset_gate: PASS/FAIL/N/A
- qc_gate: PASS/FAIL/QC_UNVERIFIED/N/A
- allowed_output: deliverable|blocked_report_only
```

If a project has an executable validator or local gate hook, run it before delivery. If no executable validator exists, record `executable_gate: N/A` and rely on documented gate evidence.

## Repository Layout

- `skills/short-drama-pipeline/SKILL.md`: trigger rules, stage routing, gate contract, and reference navigation.
- `skills/short-drama-pipeline/knowledge_compiled/`: stable compiled production rules used before raw research.
- `skills/short-drama-pipeline/references/`: detailed workflow, prompt, QC, operations, boundary, and package specs.
- `skills/short-drama-pipeline/core/combat/`: structured combat direction and prompt compiler layers.
- `skills/short-drama-pipeline/schemas/`: JSON schemas for single-shot and multi-shot combat compiler artifacts.
- `skills/short-drama-pipeline/examples/`: validated combat compiler examples.
- `skills/short-drama-pipeline/providers/`: optional provider-specific strategy notes.

## Private Overlay

Do not commit host-local overlays, private research corpora, raw API keys, provider account files, or personal filesystem paths. Add project-specific validators and route configs outside the public skill, then reference them from your project package audit.

Use private route configs if desired, but keep them provider-neutral. Name routes by capability, such as `image_asset_route`, `video_draft_route`, `video_final_route`, `audio_voice_route`, and `editing_route`, instead of assuming a specific brand.

## Quality Status

This public package has been sanitized from a local working skill. Private host paths were removed, provider-specific defaults were converted to capability routes, and combat examples/schema validation passed during packaging. Forward-testing on real short-drama tasks is still recommended before treating the skill as stable for a production pipeline.

## License

MIT. See [LICENSE](LICENSE).
