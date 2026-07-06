# Combat Canvas Integration

Use this file when turning the skill into website/app backend logic.

## Node Model

Recommended combat canvas nodes:

- `FightMapNode`: battlefield layout, combatant positions, power scale, rhythm map, escalation map, coverage plan.
- `CombatBeatNode`: tactic, counter-pressure, contact/collision, impact feedback, reaction, result state.
- `ImpactNode`: impact level, pre-impact, contact frame, hitstop, recoil, environment feedback, aftermath pose.
- `VfxPowerNode`: VFX type, source, shape, motion, color, body/environment interaction, visibility rule.
- `CameraCoverageNode`: shot type, distance, lens, motion, screen direction, subject priority, cut point.
- `ProviderRouteStrategyNode`: provider, route class, duration, references, first/end frame plan, unsupported controls, fallback route, compression rule.
- `CombatQcNode`: scoring and blockers before render.

## Backend Contract

- The app must compile single-shot combat nodes into `combat_prompt_compiler_output.json`, or multi-shot sequences into `combat_prompt_compiler_sequence.json`.
- Rendering is blocked until schema validation and Combat QC pass.
- The frontend may show director-readable Chinese text, but the backend must store structured fields, prompt hash, asset ids, model, route, seed, task id, retry count, storage keys, and QC result.
- API keys stay server-side. Frontend nodes never hold raw provider keys.
- Provider URLs must be archived into owned storage before being treated as project assets.

## UX Rule

Do not expose arrow/reference strength experiments as final logic unless the backend has recorded the crop, reference role, route, and QC outcome. Storyboards are planning artifacts; each renderable clip still needs a single selected panel/frame or a dedicated first frame.

