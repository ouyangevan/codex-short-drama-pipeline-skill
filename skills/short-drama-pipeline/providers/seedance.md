# Seedance Combat Provider Strategy

Use this provider note with `knowledge_compiled/seedance_rules.md`. Provider capabilities can change; verify current fields before production render. Keep API keys server-side.

## Seedance 2.0 Full Combat Strategy

Use for complex battle shots, avatars, domains, suppression fields, magic collisions, layered VFX, high-value contact shots, and final delivery.

Rules:

- Prefer first frame, key pose/reference image, optional end frame, and role-labeled reference images.
- Keep one primary fight intent per shot.
- Prompt may include spatial layout, action chain, contact frame, VFX layer, environment feedback, and camera motion.
- If the shot includes avatar, domain, or suppression, create an `establishing_combat_layout` or `power_reveal_wide` before the contact/impact shot.
- Required asset planning: character reference, environment reference, weapon/prop reference, first frame, optional end frame, optional VFX style reference, and optional authorized motion/audio reference.
- Full route still needs compression: do not paste the whole director layer when a structured execution prompt is enough.

## Seedance 2.0 Fast Combat Strategy

Use for drafts, short impact tests, one action, one contact, one result, or low-cost A/B testing.

Fast prompt shape:

1. Starting state.
2. One main action chain.
3. One clear contact or impact.
4. One result state.

Rules:

- Do not ask Fast to handle complex multi-stage battles, many characters, multiple spell systems, avatar plus contact plus domain in one clip, or whole storyboard grids.
- Use soft beat order instead of rigid `0-2s / 2-4s / 4-6s` timecodes unless the provider route specifically benefits from timing labels.
- Fast prompt should read like one precise director instruction, not a research memo.
- If Fast fails, downgrade the test to key-pose still creation, then image-to-video from the approved pose/frame. If the failure is route capacity, escalate to full route instead of lengthening the prompt.

## Shared Render Requirements

- References must be ordered and role-labeled before action text.
- `return_last_frame` should default to true for continuity workflows when supported.
- Store prompt hash, model, route, seed, params, asset ids, task id, usage, retry count, storage keys, and QC result.
- Archive provider `video_url` and `last_frame_url` into owned storage as soon as the task succeeds.
