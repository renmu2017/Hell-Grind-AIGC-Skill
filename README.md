<div align="center">

# Hell Grind AIGC Skill

**把创意变成可执行的提示词，把镜头连接成可追踪的作品。**

面向 AI 图片与视频创作的通用 Skill · 模型无关 · 从单张概念图到多镜头叙事

[![Version](https://img.shields.io/badge/version-v2.0.0-bb3038)](CHANGELOG.md) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-5865f2)](https://agentskills.io/specification) [![Python](https://img.shields.io/badge/local%20tools-Python%203.10%2B-3776ab)](docs/usage.md)

**简体中文** · [English](README.en.md)

[快速开始](#快速开始) · [核心优势](#核心优势) · [风格适配](#一种方法多种视觉风格) · [使用指南](docs/usage.md) · [参与贡献](CONTRIBUTING.md)

</div>

[![AFTER THE TIDE 原创概念海报：风暴后的海上气象站与黄色雨衣工程师](docs/assets/after-the-tide-poster.png)](examples/after-the-tide/README.md)

*原创视觉示例《AFTER THE TIDE》：使用本 Skill 组织提示词，通过 AI 图像工具生成。点击查看[完整提示词与制作记录](examples/after-the-tide/README.md)。这是概念海报，未制作成影片。*

Hell Grind AIGC Skill 将**提示词创作、生产管理和失败诊断**组织为一套可复用的工作流。你可以从一个画面、一条视频提示词或一份短片 brief 开始，再按需要扩展到资产、场次、镜头、生成记录、选片与交付。

Skill 以 Markdown、模板和本地脚本交付，采用 [Agent Skills](https://agentskills.io/specification) 的目录形式。支持该格式的客户端可加载整个 Skill 文件夹；其他能够阅读文件的 AI 助手也可按入口与引用使用。具体安装方式见[安装指南](docs/installation.md)。

## 核心优势

| 能力 | 创作时带来的帮助 |
| --- | --- |
| **创意与模型参数分离** | 先形成模型无关的主提示词，再单独填写平台适配层；更换工具时保留已批准的创意与约束。 |
| **保留你的原始意图** | 润色时锁定人数、角色身份、时长、逐字台词和禁止事项，并说明实际修改了什么。 |
| **从画面到完整制作** | 七层提示词架构、图片 11 类信息与视频 12 段镜头契约，连接构图、表演、摄影、声音和连续性。 |
| **把一致性落实到记录** | 14 张 schema v2 项目表追踪资产状态、参考范围、镜头、提示词版本、生成批次和选片决定。 |
| **让迭代有依据** | 六类失败诊断定位责任层，记录修改变量、假设与复测动作，为拆镜和停止迭代提供依据。 |
| **轻量、按需使用** | 一个 Skill、22 份按需读取的参考文档、3 个无第三方 Python 依赖的本地工具；单条提示词无需先建完整项目。 |

精简版用于快速探索，标准版用于日常创作，导演版用于复杂动作、对白或多镜头连续性。细节可以增减，硬约束始终保留。

## 快速开始

**先用一个镜头试试。** 下载或克隆仓库，让 AI 助手读取 `skill/hell-grind-aigc-skill/SKILL.md` 及它需要的引用文件，然后发送：

```text
使用 Hell Grind AIGC Skill，为下面的原创场景写一条标准版视频提示词：
一位成年修表师在清晨工作台前停下手中的工具，望向窗外。
恰好一人、6 秒、一个连续镜头、无对白，风格为温暖的手绘动画。
保留这些硬约束，输出主提示词、独立的平台适配层和首轮检查要点。
模型暂未指定。
```

你会得到约束快照、模型无关的主提示词、平台适配层、设计说明、假设和检查建议。模型未知时，适配层保持 `unspecified`。

<details>
<summary><strong>查看缩略示例：从一句想法到可执行的镜头设计</strong></summary>

以下为原创结构示例，省略完整评分与说明，未调用生成模型。

```text
约束：1 位成年修表师；6 秒；单镜头；无对白；温暖手绘动画。
起始状态：修表师坐在画面左侧，工作台占下方，窗户位于屏幕右侧。
动作节拍：0–2 秒放下镊子；2–4 秒视线转向窗户；4–6 秒保持侧脸，轻轻呼气。
摄影机：从胸口高度的中景缓慢直线推进，结束于含窗框边缘的侧脸近景。
风格：清晰手绘轮廓，纸面颗粒，暖米色与柔和青绿色；角色轮廓跨帧稳定。
声音：钟表滴答与轻微衣料声，无对白、无配乐。
必须保持：唯一角色、唯一镊子、窗户方向、服装配色。
平台适配：unspecified。
```

</details>

需要让客户端自动发现 Skill 时，复制整个 `skill/hell-grind-aigc-skill/` 文件夹到其支持的 skills 目录。参阅[通用安装、Claude Code 与 Codex 配置](docs/installation.md)，不要只复制入口文件。

## 原创示例：AFTER THE TIDE

**风暴过后，一位工程师修复海上气象站的信标，等待远方的回应。** 从这个独立设定出发，我们用本 Skill 定义人物、服装、道具、空间和光色，再生成海报与两张概念剧照。

<table>
  <tr>
    <td width="50%"><a href="examples/after-the-tide/README.md"><img src="docs/assets/after-the-tide-wide.png" alt="原创 AI 概念剧照：工程师站在海上气象站外，望向风暴后的海面" width="100%"></a></td>
    <td width="50%"><a href="examples/after-the-tide/README.md"><img src="docs/assets/after-the-tide-closeup.png" alt="原创 AI 概念剧照：黄色雨衣工程师的近景，窗外有一束琥珀色信标光" width="100%"></a></td>
  </tr>
  <tr>
    <td><strong>空间与环境</strong><br>用人物尺度、栈道方向、海面和气象站建立可读的空间关系。</td>
    <td><strong>表演与质感</strong><br>用视线、克制的表情、湿润衣料和冷暖光写出具体画面。</td>
  </tr>
</table>

*三张图均由本次原创提示词生成，参考输入仅使用本案例新生成的图片，未使用 Hell Grind 原作海报、剧照、角色或提示词。制作记录保留了海报道具位置的修正，以及尚未达到逐镜一致性的细节限制。*

**[查看 brief、参考范围、逐图提示词与评审 →](examples/after-the-tide/README.md)**

## 一种方法，多种视觉风格

本 Skill 将身份、空间、动作和连续性抽成通用约束，让视觉表现服从你自己的 brief。上面的案例采用写实电影风格；下面展示可以调整的表达维度，不代表已完成所有风格或跨模型生成测试。

| 视觉方向 | 重点调整 | 继续保留 |
| --- | --- | --- |
| 写实剧情 / 纪录片感 | 自然表演、有来源的光线、真实材质、克制运镜 | 身份、视线、空间与动作接点 |
| 科幻 / 奇幻 | 世界规则、尺度参照、材质反应、特效触发与落点 | 数量、位置、接触关系与状态变化 |
| 二维动画 / 漫画 | 轮廓线、色块、姿态节奏、夸张幅度 | 角色辨识度、道具归属与动作因果 |
| 水彩 / 绘本 | 纸面颗粒、边缘处理、颜色扩散、留白 | 主体数量、视觉重心与叙事顺序 |
| 产品广告 / 静物 | 产品几何、材质分区、品牌色、展示角度 | 精确文字、形状比例与使用动作 |

查看[同一场景的跨风格写法](docs/style-adaptability.md)：改变渲染、光色和运动表达，保留故事与镜头契约。

## 从一个镜头扩展到完整项目

```text
创意 brief → 资产与状态 → 场次与空间 → 镜头与提示词
                                          ↓
交付与归档 ← 剪辑与连续性 ← 评审与选片 ← 生成记录
                                          ↕
                                    诊断 → 修改 → 复测
```

需要记录完整制作时，可以直接运行本地工具。要求 Python 3.10+；在仓库根目录执行：

```bash
python3 skill/hell-grind-aigc-skill/scripts/init_project.py \
  --name "My AIGC Film" --output ./my-aigc-film

python3 skill/hell-grind-aigc-skill/scripts/validate_project.py \
  ./my-aigc-film --strict-v2 --json

python3 skill/hell-grind-aigc-skill/scripts/audit_prompt.py \
  examples/watchmaker-video.md --medium video --json
```

第三条命令审计仓库附带的[原创提示词示例](examples/watchmaker-video.md)；创作时换成你自己的文件。初始化器拒绝覆盖非空目录，两个检查工具保持只读。本地三项操作均为 **0 个网络请求、0 次数据库操作**。外部媒体生成由你选择的工具另行执行。

校验通过表示记录满足结构规则；提示词分数表示结构完整度与显式冲突检查结果。画面质量、表演效果和最终可交付性仍需实际生成、观看与评审。v1 兼容模式、目录说明和更多用法见[使用指南](docs/usage.md)。

## 文档导航

| 我想做什么 | 从这里开始 |
| --- | --- |
| 安装或接入自己的 AI 助手 | [安装指南](docs/installation.md) |
| 写图、写视频、润色或诊断失败 | [使用指南](docs/usage.md) |
| 查看真实生成案例与完整提示词 | [AFTER THE TIDE 制作记录](examples/after-the-tide/README.md) |
| 为同一创意切换视觉风格 | [风格适配示例](docs/style-adaptability.md) |
| 了解 Skill 的入口与路由 | [SKILL.md](skill/hell-grind-aigc-skill/SKILL.md) |
| 深入理解提示词与生产结构 | [七层架构](skill/hell-grind-aigc-skill/references/prompt-architecture.md) · [项目 schema](skill/hell-grind-aigc-skill/references/project-schemas.md) |
| 查看方法来源与研究限制 | [方法论证据](skill/hell-grind-aigc-skill/references/methodology-evidence.md) · [来源与许可](NOTICE.md) |
| 查看版本变化或提交改进 | [更新记录](CHANGELOG.md) · [贡献指南](CONTRIBUTING.md) |

## 来源与致谢

本项目受 Higgsfield Studio 公开的 **Hell Grind** 制作实践启发，结合通用的电影制作、资产管理与质量控制原则，独立总结并编写工作流、模板、检查工具与原创示例。原项目为方法研究提供启发，本仓库的创作案例采用独立的人物、故事与视觉设定。

**[查看 Hell Grind 官方开放项目、影片与制作说明 →](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind)**

本仓库是独立的社区项目，与 Higgsfield Studio 无官方隶属关系。当前文档展示本仓库的原创 AI 概念图；原项目材料适用其[官方许可](https://higgsfield.ai/licences/owl-p-nl-1.0)，不适用本仓库的 MIT 许可。详见 [NOTICE](NOTICE.md)。

## 参与贡献

欢迎分享可复现的失败案例、原创提示词示例、客户端接入经验、翻译和文档改进。先看[贡献指南](CONTRIBUTING.md)，再[提交 Issue](https://github.com/renmu2017/Hell-Grind-AIGC-Skill/issues) 或 Pull Request。

如果这套工作流对你有用，欢迎点亮 Star，或把它分享给一起创作的人。

## 许可证

本仓库原创代码、文档、模板与示例采用 [MIT License](LICENSE)，以维护者有权许可的范围为限。复制或分发时保留版权与许可声明；生成图片与第三方名称的说明见 [NOTICE](NOTICE.md)。
