<div align="center">

# Hell Grind AIGC Skill

**Turn creative intent into actionable prompts. Connect shots into a traceable production.**

A reusable skill for AI image and video creation · Model-agnostic · From one concept image to a multi-shot story

[![Version](https://img.shields.io/badge/version-v2.0.0-bb3038)](CHANGELOG.md) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-5865f2)](https://agentskills.io/specification) [![Python](https://img.shields.io/badge/local%20tools-Python%203.10%2B-3776ab)](docs/usage.md)

[简体中文](README.md) · **English**

[Quick start](#quick-start) · [Why use it](#why-use-it) · [Visual styles](#one-workflow-many-visual-styles) · [Usage guide](docs/usage.md) · [Contributing](CONTRIBUTING.md)

</div>

[![Official Hell Grind cover with red-and-white artwork and a character montage](https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2F32407819-ad11-4c45-a0df-96ff71e51f80.png&w=1280&q=85)](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind)

*Official cover of Hell Grind by Higgsfield Studio. Click to explore the original project. This is a source reference, not an output made with this Skill. See [NOTICE](NOTICE.md) for image credits and licensing.*

Hell Grind AIGC Skill brings **prompt crafting, production management, and failure diagnosis** into one reusable workflow. Start with an image, a video prompt, or a film brief. Add asset records, scene maps, shot contracts, generation logs, selections, and delivery checks as your project grows.

The package contains Markdown instructions, templates, and local scripts in the [Agent Skills](https://agentskills.io/specification) directory format. Compatible clients can load the complete skill folder; other assistants with file access can follow its entry point and references. See the [installation guide](docs/installation.md).

## Why use it

| Capability | What it helps you do |
| --- | --- |
| **Separate creative intent from provider settings** | Write a model-independent master prompt and keep platform parameters in a separate adapter. Retain approved decisions when changing tools. |
| **Preserve the brief** | Keep character counts, identity, duration, exact dialogue, and exclusions intact when polishing. Get a summary of what changed. |
| **Direct the whole shot** | Use seven prompt layers, 11 image information categories, and a 12-part video shot contract to connect composition, acting, camera, audio, and continuity. |
| **Track consistency explicitly** | Use 14 schema v2 tables for asset states, reference scope, shots, prompt versions, generation batches, and selection decisions. |
| **Make iteration explainable** | Diagnose six failure categories and record changed variables, hypotheses, and retests before deciding to simplify or split a shot. |
| **Use only what you need** | One skill, 22 reference documents loaded as needed, and 3 local tools with no third-party Python dependencies. A single prompt does not require a full project. |

Choose **concise**, **standard**, or **director** detail. Detail can change; hard constraints stay intact.

## Quick start

**Try one shot first.** Download or clone the repository. Ask your assistant to read `skill/hell-grind-aigc-skill/SKILL.md` and the relevant references, then send:

```text
Use Hell Grind AIGC Skill to write a standard video prompt for this original scene:
An adult watchmaker pauses at a workbench at dawn and looks toward the window.
Exactly one person, 6 seconds, one continuous take, no dialogue.
Use a warm hand-drawn animation style.
Preserve those constraints. Return the master prompt, a separate platform adapter,
and the first-test checks. The generation model is not specified yet.
```

The response includes a constraint snapshot, master prompt, platform adapter, design notes, assumptions, and review recommendations. An unknown provider stays `unspecified`.

<details>
<summary><strong>See an abbreviated example: from an idea to a shot design</strong></summary>

This original example illustrates structure. It omits the full score and commentary and has not been rendered by a generation model.

```text
Constraints: one adult watchmaker; 6 seconds; one take; no dialogue; hand-drawn animation.
Opening: watchmaker at frame-left, workbench below, window at frame-right.
Beats: 0–2s set down the tweezers; 2–4s turn gaze toward the window;
       4–6s hold the profile and exhale gently.
Camera: slow straight push from a chest-height medium shot to a profile close-up
        that retains the edge of the window frame.
Look: clean drawn contours, paper grain, warm cream and soft teal;
      preserve the character silhouette across frames.
Sound: ticking clocks and a soft fabric rustle; no dialogue or music.
Must hold: one character, one pair of tweezers, window direction, clothing colors.
Platform adapter: unspecified.
```

</details>

For automatic skill discovery, copy the entire `skill/hell-grind-aigc-skill/` folder into your client's supported skills directory. The [installation guide](docs/installation.md) covers generic setup, Claude Code, and Codex. Keep the references, scripts, and templates with the entry point.

## One workflow, many visual styles

The workflow separates identity, space, action, and continuity from the visual treatment you choose.

<table>
  <tr>
    <td width="50%"><a href="https://higgsfield.ai/@higgsfield.studio/projects/hell-grind"><img src="https://images.higgs.ai/?default=1&amp;output=webp&amp;url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2Fffd11783-e9c6-4b91-953f-587c54b77be0.jpg&amp;w=640&amp;q=85" alt="Official Hell Grind still: a wide view of a forest road and character positions" width="100%"></a></td>
    <td width="50%"><a href="https://higgsfield.ai/@higgsfield.studio/projects/hell-grind"><img src="https://images.higgs.ai/?default=1&amp;output=webp&amp;url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2F5ac07c29-b66c-46e8-93fe-c2c2a3a43461.jpg&amp;w=640&amp;q=85" alt="Official Hell Grind still: facial performance, skin texture, and side lighting" width="100%"></a></td>
  </tr>
  <tr>
    <td><strong>Space and environment</strong><br>Turn landmarks, positions, and light direction into continuity constraints.</td>
    <td><strong>Performance and texture</strong><br>Describe eyelines, facial actions, and material response as observable requirements.</td>
  </tr>
</table>

*These stills come from Higgsfield Studio's official project brief. The adaptations below are this repository's design examples, not categories of the original film or evidence of cross-model generation tests.*

| Visual direction | Adapt | Preserve |
| --- | --- | --- |
| Live-action realism / documentary feel | Restrained performance, motivated light, material texture, camera behavior | Identity, eyelines, space, action handoffs |
| Science fiction / fantasy | World rules, scale anchors, materials, effects and their timing | Counts, positions, contact, state changes |
| 2D animation / comics | Contours, color blocks, pose timing, exaggeration | Character readability, prop ownership, action causality |
| Watercolor / picture books | Paper texture, edges, pigment diffusion, negative space | Subject count, visual focus, narrative order |
| Product advertising / still life | Geometry, surfaces, brand palette, presentation angle | Exact text, proportions, product interaction |

Explore [one original scene in multiple styles](docs/style-adaptability.md), with the same story and shot constraints.

## Grow from a shot to a production

```text
Brief → Assets & states → Scenes & space → Shots & prompts
                                               ↓
Delivery ← Edit & continuity ← Review & selection ← Generation log
                                               ↕
                                      Diagnose → Revise → Retest
```

The local tools require Python 3.10+. Run them from the repository root:

```bash
python3 skill/hell-grind-aigc-skill/scripts/init_project.py \
  --name "My AIGC Film" --output ./my-aigc-film

python3 skill/hell-grind-aigc-skill/scripts/validate_project.py \
  ./my-aigc-film --strict-v2 --json

python3 skill/hell-grind-aigc-skill/scripts/audit_prompt.py \
  examples/watchmaker-video.md --medium video --json
```

The last command audits the included [original prompt example](examples/watchmaker-video.md); replace its path with your own prompt when working on a shot. Initialization refuses a non-empty destination. Both checkers are read-only. These three local operations make **zero network requests and zero database operations**. Media generation happens separately in the tool you choose.

A passing project check confirms record integrity. A prompt score reflects structural checks and explicit conflicts. Visual quality and delivery readiness still require generation, viewing, and review. See the [usage guide](docs/usage.md) for v1 compatibility and more commands.

## Documentation

| Goal | Read |
| --- | --- |
| Install or connect your assistant | [Installation](docs/installation.md) |
| Write, polish, diagnose, or audit | [Usage guide](docs/usage.md) |
| Adapt a creative idea to another visual style | [Style examples](docs/style-adaptability.md) |
| Understand the skill entry point | [SKILL.md](skill/hell-grind-aigc-skill/SKILL.md) |
| Explore production structure | [Prompt architecture](skill/hell-grind-aigc-skill/references/prompt-architecture.md) · [Project schemas](skill/hell-grind-aigc-skill/references/project-schemas.md) |
| Review methodology and evidence limits | [Research notes](skill/hell-grind-aigc-skill/references/methodology-evidence.md) · [Source credits](NOTICE.md) |
| Follow changes or contribute | [Changelog](CHANGELOG.md) · [Contributing](CONTRIBUTING.md) |

The entry point uses English with Chinese workflow labels. Detailed production references are primarily in Chinese. Request your preferred output language from your assistant; translations of the reference library are welcome.

## Source and credits

This independent community project was informed by Higgsfield Studio's publicly shared **Hell Grind** production materials.

**[Explore the official Hell Grind film, open project, and production brief →](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind)**

We are not affiliated with Higgsfield Studio. Original-film images are linked from the addresses used by the official page; they are not included in the Skill package or offered as generation assets. Source materials are subject to the [upstream license](https://higgsfield.ai/licences/owl-p-nl-1.0), not this repository's MIT license. See [NOTICE](NOTICE.md).

## Contributing

Reproducible failure cases, original prompt examples, client setup notes, translations, and documentation improvements are welcome. Read [CONTRIBUTING](CONTRIBUTING.md), then [open an issue](https://github.com/renmu2017/Hell-Grind-AIGC-Skill/issues) or submit a pull request.

If the workflow helps your work, consider starring the repository or sharing it with another creator.

## License

Original code, documentation, templates, and examples are available under the [MIT License](LICENSE). Retain the copyright and permission notice when copying or distributing. Third-party names and linked imagery are covered separately in [NOTICE](NOTICE.md).
