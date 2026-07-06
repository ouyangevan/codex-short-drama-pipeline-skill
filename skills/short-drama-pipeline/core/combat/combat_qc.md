# Combat QC

Combat QC blocks unreadable, overloaded, unsafe, or derivative battle prompts before render.

## Combat Prompt Blockers

- Only says intense fight, fast attack, epic battle, or power clash without tactical objective.
- Missing combatant positions, screen direction, or motion direction.
- Missing anticipation, contact/collision, impact, reaction, or aftermath.
- VFX hides the subject action or contact frame.
- One shot contains too many action objectives.
- Avatar, domain, or suppression has no scale contrast or spatial feedback.
- Weapon clash has only swinging, with no collision, guard, rebound, sparks, displacement, or result.
- Strike exchange has no contact point, body feedback, cloth/dust/camera feedback, or reaction.
- Constrained/fast route prompt is overloaded with multi-stage battle logic.
- A combat shot treats one action unit as the whole shot, such as only approach, crouch, stand, turn, or slow weapon raise.
- Ordinary combat coverage targets 5 seconds or more without slow motion, emotional pause, aftermath, environment reveal, or large power reveal.
- A 5-second combat shot has fewer than 6 key poses, fewer than 3 action events, or no visible force-feedback beat.
- Action events are evenly spread across the whole shot, with no front-loaded burst and no cut-ready final hold.
- Major traversal consumes most of the shot duration without tactical change, counter-pressure, contact, or result.
- Speed is described only with vague words such as fast, quickly, or rushes forward, without concrete frame-crossing or acceleration evidence.
- High-control/final route prompt lacks key-pose, first/end frame, or reference plan for complex action when the selected provider supports those controls.
- Prompt uses specific IP, identifiable character names, or direct imitation of a known work as the style target.
- Prompt includes gore, real injury detail, or real-world fighting instruction.

## Combat QC Scoring

Score each field 0-5:

- `action_readability`
- `tactical_clarity`
- `contact_believability`
- `impact_feedback`
- `spatial_continuity`
- `vfx_readability`
- `style_consistency`
- `cutability`

Any score below 4 requires rewrite before render. A score is not a vibe check; it must cite visible evidence or the missing field.

## Rhythm And Density Failure Rule

If the shot output feels slow because the prompt allowed empty time, do not solve it by adding more adjectives. Rewrite the tempo design:

- Shorten normal combat shots to 2.5-4 seconds.
- For ordinary combat shots with no slow motion, emotional pause, aftermath, environment reveal, or large power reveal, target 2.5-3.5 seconds.
- For 5 seconds or more, require 6-10 key poses, 3-5 action events, and at least 1 force-feedback beat.
- At least 60% of action events must happen in the first 70% of the shot; the final 20-30% should be landing pose, reaction, aftermath, or cut-ready hold.
- Require the main traversal to complete within 20-40% of duration unless the shot is standoff, aftermath, or environment reveal.
- Reject "approach then crouch" as insufficient even though it contains two verbs.
- `combat_qc_score.action_readability` and `combat_qc_score.cutability` must be 2 or lower when a 5-second combat shot contains only one continuous movement event.
