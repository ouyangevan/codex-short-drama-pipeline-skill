# Fight Director Layer

Use this layer before any combat storyboard, still prompt, video prompt, or render request. It is for fictional film/anime choreography only. Do not provide real-world fighting instruction, injury details, gore, or instructions that make violence easier to perform in reality. Do not copy a specific IP, character, shot, line, or identifiable house style.

## Required Output

Every combat shot must first define:

- `fight_intent`: dramatic purpose such as pressure, reversal, probing, guard break, suppression, escape, dominance, or sacrifice.
- `combatants`: each side's fictional identity, size/weapon/ability contrast, current stamina, emotional state, and current power relation.
- `tactical_objective`: what the active character tries to accomplish in this shot. Never write only "attack the enemy".
- `opponent_counter_pressure`: how the opponent makes the action difficult.
- `spatial_map`: positions, foreground/background, movement direction, obstacles, vertical level, camera axis, and screen direction.
- `action_chain`: wind-up, probe, change-up, contact/collision, impact, reaction, and result.
- `combat_tempo`: shot duration, key-pose count, action-event count, traversal window, speed curve, and force-feedback beat.
- `result_state`: who has advantage, how space changed, and how the next shot connects.
- `risk_level`: cinematic difficulty and pressure, not gore or real damage.
- `readability_plan`: how the action reads on silent autoplay through pose, screen direction, contact, reaction, and aftermath.

## Rules

- Default combat shot length is 2.5-3.5 seconds when the shot has no slow motion, emotional pause, aftermath, environment reveal, or large power reveal. Do not default ordinary combat coverage to 5 seconds.
- Use 4 seconds when the shot needs a readable contact plus reaction. Use 5 seconds or more only for standoff, emotional pause, aftermath, environment reveal, or large power reveal.
- A shot may carry only one primary fight intent, but that intent must be expressed through enough key poses and action events for the duration.
- Split large battles into layout shot, approach shot, contact shot, impact insert, reaction shot, and aftermath shot.
- Never use empty phrases such as "A and B fight intensely" as the action design.
- State who initiates, who counters, where contact happens, what visible feedback follows contact, and how the final state changes.
- If the shot cannot be understood without audio, subtitles, or lore, revise the blocking and visual evidence.

## Combat Tempo Rule

Do not treat an action unit as a whole shot. "Run forward, then crouch" is still one low-density traversal, not a complete combat shot.

Minimum density:

- 2 second combat shot: at least 3 key poses and 2 action events.
- 3 second combat shot: at least 4 key poses and 3 action events.
- 4 second combat shot: at least 5 key poses and 3 action events.
- 5 second combat shot: at least 6 key poses, 3-5 action events, and at least 1 visible force-feedback beat.

Movement speed:

- A major traversal must complete within the first 20-40% of the shot duration unless the shot is a standoff, aftermath, or environment reveal.
- Never spend an entire 5-second combat shot simply approaching a target.
- Use concrete speed evidence: "crosses half the frame within the first second", "explosive acceleration", "violent forward burst", "instant dash", "aggressive momentum".
- Avoid vague speed words alone: "fast", "quickly", "rushes forward".

Action distribution:

- Do not distribute action events evenly across the whole shot.
- At least 60% of action events must happen in the first 70% of the shot.
- The final 20-30% should be landing pose, reaction, aftermath, or cut-ready hold.
- If the final third still introduces new travel or a new attack objective, split the shot or shorten it.

Key poses must describe visible body states, not only verbs. Example: push-off, weight drop, shoulder turn, weapon parry, inside-line entry, recoil, landing.
