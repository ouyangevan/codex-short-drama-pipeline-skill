# Common Failure Cases

Use this compiled cache for fast diagnosis before searching the teaching database.

## Knowledge And Audit

- Missing cache hit or missing source entry means `knowledge_gate=FAIL`.
- Prompt-test outputs without normal-mode gate validation are draft-only.
- A stale stage artifact cannot be reused after story, character, scene, style, route, or tool capability changes.

## Assets

- Single portrait is not a character asset pack.
- Single scene mood image is not a scene spatial pack.
- Missing four-view, expression, marker/detail, or close-up blocks serious character video generation.
- Missing 720-degree/multi-angle scene pack blocks moving-camera and reverse-shot generation.
- Failed, rejected, or uninspected images cannot become start frames, end frames, storyboard references, character references, scene references, or prop references.

## Prompt And Motion

- Reference uploads without order and role labels are invalid.
- A storyboard/mid-action frame cannot be used as the start frame.
- An ending/result frame cannot be used as the cause/start frame.
- If first/end frames are not a plausible physical chain, add intermediate frames or split the shot.
- More than three clear beats in 5 seconds usually needs splitting or a longer duration.
- Fight prompts fail when they name motion but omit tactical intent, start/end spatial relation, first visible contact, opponent reaction, force direction, prop state, or end-state handoff.
- `fight_final` failure diagnosis order: action overload, missing contact visibility, unclear spatial axis, reaction not bound to contact, VFX occluding action, camera competing with action, prop binding missing, style conflict, model route too weak.
- Do not repair a failed fight by rewriting everything. Preserve the successful story, identity, scene, style, and reference bindings; change one primary variable per retry.
- If Fast fails twice because space, contact, VFX, opponent reaction, or prop continuity collapses, escalate route or split the shot instead of continuing to lengthen the prompt.

## Video And Edit

- Identity swaps, face collapse, wrong target/action, continuity breaks, random text, watermarks, subtitles, UI, or mouth/dialogue conflict are blockers.
- Frozen-tail padding used to cover dialogue is a QC failure unless explicitly approved as a deliberate freeze-frame effect.
- Generated background ambience, crowd chatter, room tone, BGM, songs, or duplicate voice must be removed or regenerated.

## AI Combat Failure Library

Each combat failure needs `symptom`, `likely_cause`, `fix_rule`, and `rewrite_example`.

| Failure | Symptom | Likely cause | Fix rule | Rewrite example |
|---|---|---|---|---|
| `floating_action` | Character drifts or floats without weight. | No foot plant, root motion, gravity, or landing state. | Add grounded start/end pose, foot contact, weight shift, and recoil. | "hero plants left foot in puddle, pushes forward, lands with right knee bent and water ripple under boot" |
| `fake_contact` | Attack passes near target with no readable touch. | Contact point not named or VFX/camera hides it. | State first visible contact point and hold/reaction. | "blade spine clearly hits the middle of the spear shaft at center frame before sparks appear" |
| `no_recoil` | Target is hit but nobody reacts. | Reaction not bound to contact. | Put reaction after contact and match force direction. | "after the shield impact, enemy shoulder turns back and rear foot slides half a step" |
| `vfx_soup` | Full-screen glow makes action unreadable. | VFX has no attachment, visibility rule, or decay. | Bind VFX to source/contact/environment and keep contact clear. | "gold impact wave expands from the palm contact and stays below chest height" |
| `teleport_combat` | Characters jump positions between shots. | Missing spatial map and continuity out/in. | Preserve screen direction, facing, distance, and reset shots. | "enemy remains screen left in half-kneel; next shot starts from the same left-front position" |
| `multi_action_overload` | One clip tries to show a whole fight. | Too many tactical objectives/contact events/camera moves. | Split into layout, approach, contact, reaction, aftermath. | "Shot A: approach; Shot B: weapon contact; Shot C: reaction and floor seal" |
| `no_tactical_meaning` | Many movements happen but viewer cannot tell who is winning. | No fight intent, tactical objective, or result state. | Add objective, counter-pressure, and power-state change. | "hero blocks the spear to stop retreating and pin the enemy's weapon to screen left" |
| `scale_mismatch` | Avatar/giant form feels same size as humans. | No scale anchor. | Add small human, shadow, floor marks, clouds, or wide reveal. | "avatar shadow covers the stairs while the hero remains small in the foreground" |
| `weak_suppression` | Suppression is only a light effect. | No spatial pressure or environment response. | Show heavy space through posture, floor, air, debris, cloth. | "floor lines flare, stones press flat, enemy cloak is pulled downward" |
| `weapon_without_resistance` | Weapon looks like a light stick passing through objects. | No collision, vibration, rebound, grip pressure, or displacement. | Add clash point, weapon vibration, rebound, and result. | "staff strikes the blade, bends slightly, rebounds left, enemy hand tightens" |
| `fast_model_overload` | Low-control/fast route ignores camera/action/VFX details. | Prompt asks a constrained route for a final-complexity shot. | Reduce to one action/contact/result, split the shot, or escalate route. | "locked medium shot, one staff-to-blade clash, sparks, rebound, planted end pose" |
