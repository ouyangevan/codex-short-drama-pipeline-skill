# Boundaries

## This Skill

`short-drama-pipeline` is for repeatable AI short-drama production:

- idea to project package
- story bible
- episode script
- character bible
- scene bible
- storyboard
- still and video prompts
- QC gates
- overseas release pack
- batch iteration

It optimizes for repeatability, consistency, cost control, review gates, and series production.

## Existing Skills

Use `high-tech-short-video` when the user wants:

- premium high-tech vertical video
- Apple/Google/NVIDIA-style launch promo
- founder/company/product story
- rendered MP4
- tight caption sync
- real source material and research

For one-off video prompt polishing outside a short-drama project:

- handle it as a normal prompt task without invoking a separate local skill
- if it belongs to a short-drama project, use this skill's `references/prompt-rules.md` and `references/qc-gates.md`
- still apply camera motivation, action phase, reference binding, and physical logic checks

For 小云雀 / xyq or any external creative-agent platform:

- treat the platform as a tool route inside this pipeline only when the user explicitly selects it
- upload only assets that already passed the pipeline's knowledge, asset, and QC gates
- submit the approved prompt package without letting the platform bypass source reading, frame-phase rules, or final QC

## Ambiguous Requests

If the user says “帮我做短剧”:

- If they mention workflow, batch, series, project package, or automatic pipeline, use this skill.
- If they mention one polished rendered MP4, premium visual quality, tech/business promo, or captioned final video, use `high-tech-short-video`.
- If they only ask for a video prompt inside a short-drama project, use this skill's prompt/QC references; if outside the project, handle it as a one-off prompt task.
- If they mention 小云雀 or another creative-agent platform, ask whether it is the selected tool route for this pipeline run.

If still ambiguous, ask one concise question: “你要流水线短剧项目包，还是一条高质量成片？”

## Boundaries

Activation rule:

Use this skill only when the user explicitly asks to generate, produce, plan, or run an AI short-drama project or short-drama pipeline. Do not activate it merely because a task mentions this skill, video APIs, prompt engineering, a local program, a website, model routes, or files inside this skill.

Use this skill for:

- AI 短剧流水线
- 批量短剧 / 系列短剧
- 从想法生成故事包、角色、场景、分镜、提示词、质检、发布包
- 低成本试错、可复盘、可迭代的短剧生产
- 用户说“按流程做短剧”“做一套短剧项目包”“以后我给想法你自动跑”

Do not use this skill for:

- Premium tech launch videos, founder stories, product promos, or rendered high-end MP4s. Use `high-tech-short-video`.
- Isolated non-series AI video prompt polishing. Use this skill's `references/prompt-rules.md` only when the prompt belongs to the short-drama pipeline; otherwise handle it as a one-off prompt task without invoking a separate local skill.
- General Codex work such as writing programs, building websites, debugging software, adding APIs, creating local tools, reading docs, searching the web, managing files, or architecting an app. For those tasks, use normal software-development skills and read this skill only as a requirements document if the user asks to build tooling around it.
- Building a short-drama factory application, web UI, API wrapper, validator, or automation around this pipeline. Treat the skill as product requirements for that software project; do not run the short-drama production workflow unless the user also explicitly asks to generate an actual short-drama project.
- Directly generating or editing through external creative-agent platforms such as 小云雀 / xyq unless the user explicitly selects that route for the current run. Treat those platforms as tool routes inside the pipeline, not as separate short-drama skills.
- Fully automated upload to Vidu, Runway, TikTok, YouTube, or other platforms unless the user explicitly provides account access and asks for that integration.

If the user asks for “高质量短剧” and expects one polished cinematic rendered video, ask whether they mean `high-tech-short-video` style output or this repeatable pipeline. If they ask for “流水线短剧”, “批量短剧”, “短剧工作流”, or “自动化短剧生产”, use this skill.
