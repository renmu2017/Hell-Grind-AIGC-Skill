# 参与贡献 / Contributing

感谢你帮助更多创作者使用这套工作流。我们优先接受能让任务更清楚、示例更可复现、工具更可靠的改进。

Help make the workflow easier to use, examples easier to reproduce, and tools more reliable.

## 欢迎哪些贡献 / Useful contributions

- **真实失败案例 / Failure cases** — 原提示词、硬约束、观察到的问题和最小复测方案。 / Include the original prompt, hard constraints, observed problem, and a minimal retest.
- **原创示例 / Original examples** — 展示一种具体技巧，标明是设计示例还是实际生成结果。 / Demonstrate one technique and distinguish a design example from a generated result.
- **接入经验 / Client setup** — 客户端与版本、安装位置、验证方式和限制。 / Document the client version, install location, validation, and limits.
- **翻译与编辑 / Translation and editing** — 保持中英文首页的能力声明、示例约束和链接一致。 / Keep capability claims, example constraints, and links aligned across both READMEs.
- **工具修复 / Tool fixes** — 提供最小复现，解释触发条件与影响。 / Supply a minimal reproduction, trigger, and impact.

提交前可先[查看现有 Issues](https://github.com/renmu2017/Hell-Grind-AIGC-Skill/issues)。涉及工作流或 schema 的大改动，先开 Issue 说明目标；小幅文档改进可以直接提交 PR。

Check [existing issues](https://github.com/renmu2017/Hell-Grind-AIGC-Skill/issues) first. Discuss substantial workflow or schema changes in an issue; small documentation improvements can go straight to a pull request.

## 一个好的 Issue / A useful issue

```text
Goal / 目标:
Client, version, OS / 客户端、版本、系统:
Steps or original prompt / 步骤或原提示词:
Hard constraints / 硬约束:
Expected / 预期:
Observed / 实际:
Minimal example / 最小示例:
```

只提供与复现有关的材料。移除密钥、账户信息和私人项目数据；媒体或提示词必须是你有权分享的内容。

Include only material needed to reproduce the issue. Remove credentials, account details, and private project data; share only media and prompts you have permission to distribute.

## 提交改动 / Submit a change

1. Fork 仓库并为改动建立分支。 / Fork the repository and create a focused branch.
2. 保留一个父 Skill 与按需引用结构，避免重复粘贴规则。 / Preserve one parent skill and its focused references; avoid duplicating instructions.
3. 按改动范围验证。文档检查链接、锚点、示例和图片；脚本与契约变化运行现有测试。 / Validate in proportion to the change: check links, anchors, examples, and images for docs; run the existing tests for script or contract changes.
4. 在 PR 中写清问题、结果和实际验证。 / Explain the problem, resulting behavior, and checks performed in the PR.

仓库现有检查 / Existing checks:

```bash
python3 -m unittest discover -s tests -v
git diff --check
```

本地初始化、校验和审计须继续保持离线；校验器保持只读，初始化器不得覆盖非空目标。结构校验不能替代实际媒体评审。

Keep initialization, validation, and auditing offline. Validators remain read-only, and initialization must refuse a non-empty destination. Structural checks do not replace visual review.

## 文档原则 / Documentation principles

写清用户能完成什么，给出最短可用示例，再链接到详细方法。展示现有能力；对设想、历史样本和未验证接入明确标注。图片有准确描述、来源链接与作者署名，原作画面不得写成本 Skill 的生成案例。

Lead with the outcome, provide a small usable example, then link to details. Describe implemented capabilities and label proposals, historical samples, and unverified integrations. Give images accurate descriptions, source links, and creator credits; do not present source-film imagery as outputs of this Skill.

本次文档结构参考了 [Ollama](https://github.com/ollama/ollama) 的简洁入门、[ComfyUI](https://github.com/Comfy-Org/ComfyUI) 的视觉展示与功能导航，以及 [Anthropic Skills](https://github.com/anthropics/skills) 的 Skill 组织和示例说明。参考的是信息组织方式，不复制其品牌、文案或素材，也不暗示关联或背书。

The documentation structure takes cues from [Ollama](https://github.com/ollama/ollama)'s concise onboarding, [ComfyUI](https://github.com/Comfy-Org/ComfyUI)'s visual presentation and feature navigation, and [Anthropic Skills](https://github.com/anthropics/skills)' skill organization and examples. These are structural references, not copied branding, wording, assets, or endorsements.

## 许可 / License

原创贡献按仓库 [MIT License](LICENSE) 提交。第三方图片和来源材料有独立许可；请阅读 [NOTICE](NOTICE.md)，不要把原项目素材包或全量提示词提交到本仓库。

Original contributions are submitted under the repository's [MIT License](LICENSE). Third-party images and source materials have separate terms; read [NOTICE](NOTICE.md) and do not submit source asset packs or bulk prompt datasets.
