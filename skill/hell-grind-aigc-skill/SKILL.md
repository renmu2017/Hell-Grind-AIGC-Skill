---
name: hell-grind-aigc-skill
description: Use when structuring, managing, auditing, or diagnosing an AIGC video project; creating or polishing model-agnostic image and video prompts; or tracking assets, shots, generations, and continuity while preserving creative intent and hard constraints.
---

# Hell Grind AIGC Skill

Use this Skill as a model-agnostic AIGC production workflow in an AI assistant or agent that can read its instructions and supporting files. Keep approved project facts, creative instructions, provider settings, generation attempts, and review decisions separate. Local scripts require Python 3.10+; prompt writing itself does not require a shell or a generation API.

Adapt the visual language to the user's brief: live-action realism, stylized animation, illustration, product imagery, or another explicitly chosen medium. Preserve identity, counts, spatial relationships, timing, and continuity while changing rendering, materials, lighting, and motion conventions. Do not carry photorealistic skin, natural-light rules, or physical-camera language into a style where they conflict with the brief.

Use the user's requested output language. References contain Chinese and English production terminology; client-specific UI metadata is optional and does not change the core workflow.

## Classify the request

Determine these dimensions before writing:

- Workflow: 生产管理 / 提示词创作 / 失败诊断.
- Medium: image / video / mixed project.
- Operation: create / polish / initialize / audit / diagnose.
- Richness: 精简版 / 标准版 / 导演版.
- Context: standalone prompt / existing project.
- Provider: unspecified / named without adaptation / explicit adaptation requested.
- Authority: text only / local files / media generation / upload or publication.

## Route to the minimum references

For any non-trivial prompt, first read `references/prompt-architecture.md`. Read `references/methodology-evidence.md` when explaining why the workflow uses assets, versions, iteration, or risk gates.

### 生产管理工作流

For project setup, tracking, continuity, review, or delivery, read:

- `references/production-workflow.md`
- `references/project-schemas.md`
- `references/project-qa-gates.md` for audit or delivery

### 提示词创作工作流：图片从零生成 / 图片润色扩写

Read:

- `references/image-prompt-crafting.md`
- `references/reference-asset-control.md` for asset sheets, identity/state versions, or reference inheritance
- `references/spatial-blocking.md` for multiple subjects, exact placement, screen direction, or unique props
- `references/prompt-preservation.md`
- `references/prompt-quality-rubric.md`

### 视频从零生成 / 视频润色扩写

Read:

- `references/video-prompt-contract.md`
- `references/camera-editing-language.md` for framing, lens effect, movement, focus, cuts, or camera failures
- `references/performance-direction.md` for acting, eyelines, breath, dialogue performance, or stillness
- `references/action-physics-vfx.md` for movement, impact, fights, throws, destruction, creatures, or effects
- `references/spatial-blocking.md` for exact placement, direction, axis, and unique objects
- `references/lighting-color-material.md` for motivated light, exposure, palette, surfaces, or weather
- `references/dialogue-audio.md` for exact dialogue, lips, ambience, foley, silence, or mix
- `references/continuity-control.md` for cross-shot identity, state, axis, action, environment, or sound
- `references/negative-constraints.md` when selecting and compressing failure-specific avoid rules
- `references/multi-shot-sequences.md` for cuts, dialogue coverage, action sequences, or montage
- `references/prompt-preservation.md`
- `references/prompt-quality-rubric.md`

### 失败诊断

Read `references/failure-diagnosis.md`, then the affected layer guide. Start with the relevant quality gate and production record. Identify whether the defect belongs to the asset, scene/shot contract, prompt, provider adapter, generation attempt, or edit. Do not default to adding more negative words.

For identity drift, inspect the approved asset state and reference scope first; do not begin by expanding negative constraints.

For repeated generations, candidate comparison, version changes, or budget/stop decisions, read `references/iteration-selection.md`.

Read `references/prompt-examples.md` only when an example materially helps. For work inside an existing project, first load its approved asset, scene, shot, prompt version, generation, selection, and continuity records.

## Work in this order

1. Extract intent, hard constraints, reference scope, output use, and authority.
2. Preserve explicit counts, duration, exact text/dialogue, identity, state, rights, and prohibited content.
3. Ask only when a missing fact would materially change the result; otherwise state a conservative assumption.
4. Build a model-independent artifact, then place provider-specific settings in a separate platform adapter.
5. Check IDs, references, timing, spatial logic, continuity, contradictions, and current quality gates.
6. Return the artifact with the fixed output required by its reference.

## Choose richness deliberately

- **精简版**: low-complexity exploration; keep only result-determining facts.
- **标准版**: default production form; cover the complete image or shot contract without repeating approved facts.
- **导演版**: complex action, dialogue, multi-character, multi-shot, or strict-continuity work; expose timing, performance, camera endpoints, audio, continuity, and risk locks.

Richness changes detail, never the user's intent or hard constraints.

## Initialize or audit a project

Run the bundled scripts when local file creation is requested:

```bash
python3 scripts/init_project.py --name "Project name" --output /absolute/project/path
python3 scripts/validate_project.py /absolute/project/path --strict-v2
python3 scripts/audit_prompt.py /absolute/prompt.md --medium video
```

The initializer must refuse a non-empty target. The validator must remain read-only. Do not replace these safety behaviors with ad hoc file operations.

## Fixed prompt output

Unless the user asks for a narrower artifact, return:

1. Mode and richness.
2. Intent and hard-constraint snapshot.
3. Model-independent master prompt.
4. Separate platform adapter; write `unspecified` when unknown.
5. Design summary for new prompts or modification summary for polishing.
6. Assumptions and unresolved choices.
7. Quality score with concrete deductions.
8. Risks and first-test recommendation.

## Preserve boundaries

- 默认不调用付费模型，不上传、不发布、不部署。
- Do not treat prompt writing as authorization to generate media.
- Do not invent an authorization, budget, provider, reference right, or delivery approval.
- Do not copy project-specific Hell Grind characters, assets, or long source prompts into a new project unless the user separately supplies rights and requests reuse.
- Keep each local initialize/validate/audit operation at 0 network requests and 0 database operations.

If the user explicitly requests generation or publication, treat it as a separate action and follow the active tool's confirmation, cost, and safety rules.
