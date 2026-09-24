# 安装与接入 / Installation

[中文首页](../README.md) · [English overview](../README.en.md) · [使用指南 / Usage](usage.md)

## 选择接入方式 / Choose a setup

Skill 核心是一个可携带的文件夹。选择方式取决于你的 AI 助手如何加载指令；图片或视频生成平台可以另外选择。

The core is a portable folder. Your assistant determines how instructions are loaded; your image or video generation provider is a separate choice.

| 使用方式 / Setup | 做法 / Action | 要求 / Requirement |
| --- | --- | --- |
| 直接使用 / Read directly | 让助手读取 `SKILL.md` 及相关引用 / Ask the assistant to read the entry point and needed references | 能读取文件或接收你提供的文本 / File access or supplied text |
| 原生 Skills 客户端 / Native skills client | 复制完整 Skill 文件夹到客户端认可的目录 / Copy the complete folder to its supported directory | 客户端支持该目录和格式 / Client support for the directory and format |
| 本地命令 / Local tools | 从仓库直接执行 3 个 Python 工具 / Run the three Python tools directly | Python 3.10+ |

提示词创作不要求 Python。脚本只使用 Python 标准库。下文的安装命令使用 macOS/Linux 的 shell；Windows 用户可以手动复制文件夹，并使用可用的 Python 3.10+ 命令运行工具。

Prompt writing does not require Python. The scripts use only the Python standard library. Shell examples below target macOS/Linux; on Windows, copy the folder manually and use your Python 3.10+ executable for the local tools.

## 获取文件 / Get the files

```bash
git clone https://github.com/renmu2017/Hell-Grind-AIGC-Skill.git
cd Hell-Grind-AIGC-Skill
```

也可在 GitHub 的 **Code → Download ZIP** 中下载后解压。

You can also use **Code → Download ZIP** on GitHub and extract the archive.

需要保留的完整结构 / Keep this complete structure:

```text
skill/hell-grind-aigc-skill/
├── SKILL.md                 # Entry point
├── VERSION
├── references/              # 22 guides, loaded as needed
├── assets/project-template/ # Production records and templates
├── scripts/                 # Initialize, validate, audit
└── agents/openai.yaml       # Optional client UI metadata
```

`agents/openai.yaml` 为支持它的客户端提供显示信息；核心工作流不依赖这个文件。不要只复制 `SKILL.md`，否则引用、模板和工具会缺失。

`agents/openai.yaml` supplies optional UI metadata to clients that recognize it. It does not define the core workflow. Copying only `SKILL.md` leaves its references, templates, and tools unavailable.

## 通用接入 / Generic setup

让助手读取仓库中的入口，不需要安装脚本：

Ask your assistant to read the entry point directly; no installer is required:

```text
Read skill/hell-grind-aigc-skill/SKILL.md and follow the references relevant to my request.
Use Hell Grind AIGC Skill to draft a standard image prompt from the brief below.
Keep the provider unspecified and respond in my preferred language.
Brief: ...
```

如果客户端支持自动发现 Skills，按照它的官方说明，将 `hell-grind-aigc-skill` 整个目录放进其 skills 目录。若目录中已有同名 Skill，先将原目录移出到自己的备份位置，再放入新版本。

For automatic discovery, follow your client's documented skills-directory convention and place the complete `hell-grind-aigc-skill` folder there. If a copy already exists, move it to a separate backup location before installing the new version.

## Claude Code

按 [Claude Code 官方文档](https://code.claude.com/docs/en/skills)，个人 Skills 放在 `~/.claude/skills/`，项目 Skills 放在项目的 `.claude/skills/`。以下示例安装个人 Skill，仅在目标不存在时复制：

[Claude Code documents](https://code.claude.com/docs/en/skills) `~/.claude/skills/` for personal skills and `.claude/skills/` within a project. This personal-install example copies only when the destination is absent:

```bash
mkdir -p "$HOME/.claude/skills"
if [ ! -e "$HOME/.claude/skills/hell-grind-aigc-skill" ]; then
  cp -R skill/hell-grind-aigc-skill "$HOME/.claude/skills/"
else
  echo "Skill already exists. Back up the existing folder before replacing it."
fi
```

用 `/hell-grind-aigc-skill` 显式调用，或在请求中写明 Skill 名称。

Invoke it explicitly with `/hell-grind-aigc-skill`, or name it in your request.

## Codex

仓库原有安装脚本是 Codex 的便捷入口：

The bundled installer is a convenience option for Codex:

```bash
./scripts/install.sh
```

它安装到 `${CODEX_HOME}/skills/hell-grind-aigc-skill`；未设置 `CODEX_HOME` 时使用 `~/.codex/skills/hell-grind-aigc-skill`。重新打开任务以刷新 Skill 列表，再通过 `$hell-grind-aigc-skill` 调用。

It installs to `${CODEX_HOME}/skills/hell-grind-aigc-skill`, or `~/.codex/skills/hell-grind-aigc-skill` when `CODEX_HOME` is unset. Open a new task to refresh discovery and invoke it with `$hell-grind-aigc-skill`.

更新 / Update:

```bash
git pull --ff-only
./scripts/install.sh --update
```

`--update` 将原目录移到 Skills 根目录内的 `.backups/` 后安装新版本。该脚本不负责其他客户端的安装。

`--update` moves the existing folder into `.backups/` under the skills root before installing the new copy. This script does not install into other clients.

## 确认接入 / Check the setup

发送一个简单请求，例如：“用本 Skill 写一条 6 秒、单人、无对白的视频提示词，保留模型未知。”确认助手能读取入口和所需引用，输出约束快照、主提示词和独立适配层。需要本地工具时，再按[使用指南](usage.md)运行初始化与严格校验。

Try a small request: “Use this Skill for a six-second video prompt with one person, no dialogue, and an unspecified model.” Confirm that the assistant can read the entry point and required references, and returns the constraints, master prompt, and separate adapter. For local tools, follow the [usage guide](usage.md).

这里说明的是文件格式、路径和接入方式，不代表所有客户端、模型或版本都已完成端到端验证。若接入失败，请在 Issue 中附上客户端版本、安装位置和实际错误。

These instructions describe packaging and setup, not an end-to-end certification of every client, model, or version. If discovery fails, report the client version, install location, and observed error in an issue.
