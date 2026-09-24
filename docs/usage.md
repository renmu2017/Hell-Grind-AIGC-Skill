# 使用指南 / Usage guide

[中文首页](../README.md) · [English overview](../README.en.md) · [安装 / Installation](installation.md)

## 从你的任务开始 / Start with your task

| 任务 / Task | 给助手的请求 / Example request |
| --- | --- |
| 图片创作 / Image prompt | 用 Hell Grind AIGC Skill 为原创雨夜维修站写标准版图片提示词，模型未知。 / Write a standard image prompt for an original rain-soaked repair station, provider unspecified. |
| 视频创作 / Video prompt | 设计 6 秒单镜头，恰好一名角色，输出起止状态、动作节拍和摄影机终点。 / Design a six-second take with one character, opening and closing states, action beats, and a camera endpoint. |
| 润色 / Polish | 润色下面的提示词，保留两人、6 秒和逐字台词，列出修改摘要。 / Polish this prompt while keeping two characters, six seconds, and the exact dialogue; explain the changes. |
| 失败诊断 / Diagnose | 诊断身份漂移和左右反转，先定位资产或空间问题，再给最小修复与复测变量。 / Diagnose identity drift and reversed screen direction; locate the asset or spatial issue and suggest a minimal retest. |
| 生产管理 / Production | 将这份 brief 搭成 schema v2 项目，先建立资产、场次、空间与镜头记录。 / Initialize a schema v2 project from this brief, starting with assets, scenes, spatial layout, and shots. |
| 项目审核 / Audit | 只读检查资产版本、镜头、生成记录、选片和连续性。 / Audit asset versions, shots, generation logs, selections, and continuity without changing records. |

需要时附上完整 brief、原提示词、已批准资产和具体失败表现。只有文字描述时，诊断应标为基于描述的假设；实际图像或视频仍需观看。

Supply the brief, original prompt, approved assets, and observed failures where available. With text descriptions alone, treat the diagnosis as a hypothesis; actual media still needs visual review.

## 选择输出深度 / Choose detail

| 模式 / Mode | 适用场景 / Use |
| --- | --- |
| 精简版 / Concise | 快速探索与简单主体 / Exploration and simple subjects |
| 标准版 / Standard | 日常图片与单镜头创作 / Everyday images and individual shots |
| 导演版 / Director | 对白、多人、复杂动作与连续镜头 / Dialogue, multiple subjects, complex action, continuity |

通常输出：模式与深度、意图与硬约束、主提示词、独立平台适配层、设计或修改摘要、假设、质量评分与扣分理由、首轮检查建议。用户可以指定更窄的输出范围。

The usual response includes mode and detail, intent and constraints, master prompt, separate adapter, design or revision notes, assumptions, a score with deductions, and first-test recommendations. Ask for a narrower artifact when that is all you need.

## 本地工具 / Local tools

要求 Python 3.10+，不需要第三方 Python 包。以下命令在仓库根目录执行；将示例路径替换为实际项目路径。

Requires Python 3.10+ with no third-party packages. Run these commands from the repository root and replace example paths with your project paths.

### 初始化 / Initialize

```bash
python3 skill/hell-grind-aigc-skill/scripts/init_project.py \
  --name "My AIGC Film" \
  --output ./my-aigc-film \
  --project-id PRJ-MY-FILM-001 \
  --aspect-ratio 16:9
```

创建 schema v2 项目；目标必须不存在或为空目录。项目先在临时目录组装，再移动到目标。新建模板不代表已有获批资产、真实生成或交付批准。

Creates a schema v2 project in a new or empty directory. Files are assembled in a temporary directory before moving into place. An initialized template does not imply approved assets, completed generations, or delivery approval.

### 项目校验 / Validate

```bash
python3 skill/hell-grind-aigc-skill/scripts/validate_project.py \
  ./my-aigc-film --strict-v2 --json
```

只读检查表头、ID、状态、引用、时间线、成本和提示词/生成/选片关系。`--strict-v2` 要求 v2 的表和规则。省略 `--json` 可查看面向人的报告。

Checks headers, IDs, states, references, timelines, costs, and prompt/generation/selection relationships without changing the project. `--strict-v2` requires v2 tables and rules. Omit `--json` for a human-readable report.

### 提示词审计 / Audit a prompt

```bash
python3 skill/hell-grind-aigc-skill/scripts/audit_prompt.py \
  examples/watchmaker-video.md --medium video --json
```

上面审计仓库附带的[原创提示词示例](../examples/watchmaker-video.md)。写完自己的提示词后，将路径换成对应文件。图片提示词使用 `--medium image`；也支持标准输入：

The command audits the included [original prompt example](../examples/watchmaker-video.md). Replace the path with your own prompt when ready. Use `--medium image` for image prompts. Standard input is also supported:

```bash
printf '%s' '画面中恰好一名成年修表师，坐在工作台左侧。' | \
  python3 skill/hell-grind-aigc-skill/scripts/audit_prompt.py - --medium image
```

短例可能被指出缺少信息，这是审计器的正常用途。它检查缺失模块和显式冲突，例如静止与运动矛盾、多主运镜、时间越界、参考范围缺失和平台参数混入。它不观看媒体，不预测生成效果。

A short example may receive missing-information findings; that is expected. The auditor checks structure and explicit conflicts such as incompatible motion, competing camera moves, timing overruns, missing reference scope, and provider parameters mixed into the master prompt. It does not watch media or predict visual quality.

本地初始化、校验、审计均为 **0 个网络请求、0 次数据库操作**。Skill 本身不带模型调用连接器；媒体生成、费用和发布由实际使用的工具及用户授权决定。

Initialization, validation, and auditing make **zero network requests and zero database operations**. The Skill has no built-in generation connector; media generation, costs, and publication depend on the chosen tool and user authorization.

## 项目结构 / Project structure

```text
00_brief/        Configuration, goals, budget, authority
01_story/        World rules, story, visual and sound motifs
02_assets/       Assets, reference scope, state versions
03_scenes/       Scenes and spatial maps
04_shots/        Shots, action beats, audio cues
05_prompts/      Prompt index, master prompts, platform adapters
06_generations/  Generation records and iteration hypotheses
07_review/       Selections, continuity, quality gates, waivers
08_edit/         Editing, sound, subtitles, color, post-production
09_delivery/     Technical checks, rights, archive, release approval
```

完整字段与关系见 [Project schemas](../skill/hell-grind-aigc-skill/references/project-schemas.md)。生成记录应填写真实结果；未知模型、成本或状态不得当作已确认数据。

See [Project schemas](../skill/hell-grind-aigc-skill/references/project-schemas.md) for fields and relationships. Record real attempts; do not fill unknown providers, costs, or statuses as confirmed facts.

## v1 项目 / v1 projects

```bash
python3 skill/hell-grind-aigc-skill/scripts/validate_project.py \
  /absolute/path/to/v1-project --json
```

默认模式读取 `schema_version: 1` 并给出迁移提醒；`--strict-v2` 要求 v2。工具不自动迁移或改写旧项目。需要迁移时保留原文件，再建立 v2 记录。

Default mode accepts `schema_version: 1` with a migration warning; `--strict-v2` requires v2. The tools do not migrate or rewrite an existing project. Preserve originals when preparing a v2 migration.

## 常见问题 / FAQ

**能接任何模型吗？ / Does it work with any model?**

主提示词与生产记录不绑定模型。实际时长、参考图、声音、运镜和参数能力取决于所选平台，需要单独适配与试生成。

Master prompts and production records are model-independent. Duration, references, audio, motion, and parameters depend on the provider and require adaptation and test generations.

**通用 Skill 等于自动生成视频吗？ / Does the Skill generate video automatically?**

Skill 提供工作方法和本地记录工具。生成需要另外接入工具；单纯写提示词不会触发媒体生成。

It supplies instructions and local record tools. Generation needs a separate tool; asking for a prompt does not itself trigger media generation.

**为什么换画风后还要检查？ / Why review after changing styles?**

风格会改变轮廓、材质和动作表达。即使主体数量与时间线没有改变，也要检查身份、道具和镜头接点是否仍然清楚。

Style changes affect contours, materials, and motion. Even with unchanged counts and timing, review identity, props, and shot handoffs. See [style examples](style-adaptability.md).
