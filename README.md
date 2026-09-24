<div align="center">

# Hell Grind AIGC Skill

**把创意变成可执行的提示词，把镜头连接成可追踪的作品。**

面向 AI 图片与视频创作的通用 Skill · 模型无关 · 从单张概念图到多镜头叙事

[![Version](https://img.shields.io/badge/version-v2.0.0-bb3038)](CHANGELOG.md) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-5865f2)](https://agentskills.io/specification) [![Python](https://img.shields.io/badge/local%20tools-Python%203.10%2B-3776ab)](docs/usage.md)

**简体中文** · [English](README.en.md)

[快速开始](#快速开始) · [核心优势](#核心优势) · [风格适配](#一种方法多种视觉风格) · [使用指南](docs/usage.md) · [参与贡献](CONTRIBUTING.md)

</div>

[![Hell Grind 官方封面：红白色主视觉与角色拼贴](https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2F32407819-ad11-4c45-a0df-96ff71e51f80.png&w=1280&q=85)](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind)

*配图：Higgsfield Studio《Hell Grind》官方封面，点击查看原项目。它展示本 Skill 的研究来源，不是本 Skill 生成的作品。图片来源与许可见 [NOTICE](NOTICE.md)。*

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

## 一种方法，多种视觉风格

Hell Grind 原作提供了研究素材。本 Skill 将身份、空间、动作和连续性抽成通用约束，让视觉表现服从你自己的 brief。

<table>
  <tr>
    <td width="50%"><a href="https://higgsfield.ai/@higgsfield.studio/projects/hell-grind"><img src="https://images.higgs.ai/?default=1&amp;output=webp&amp;url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2Fffd11783-e9c6-4b91-953f-587c54b77be0.jpg&amp;w=640&amp;q=85" alt="Hell Grind 官方剧照：林间道路全景与人物站位" width="100%"></a></td>
    <td width="50%"><a href="https://higgsfield.ai/@higgsfield.studio/projects/hell-grind"><img src="https://images.higgs.ai/?default=1&amp;output=webp&amp;url=https%3A%2F%2Fd2ol7oe51mr4n9.cloudfront.net%2Fuser_3DceaodfgWmy2JKTLmokw2y8gJA%2F5ac07c29-b66c-46e8-93fe-c2c2a3a43461.jpg&amp;w=640&amp;q=85" alt="Hell Grind 官方剧照：人物近景中的视线、皮肤质感与侧光" width="100%"></a></td>
  </tr>
  <tr>
    <td><strong>空间与环境</strong><br>道路、人物位置与光线方向，都可以写成镜头之间需要保持的约束。</td>
    <td><strong>表演与质感</strong><br>视线、面部动作与材质响应，可以写成具体的表演和视觉要求。</td>
  </tr>
</table>

*以上两图均引自 Higgsfield Studio 官方项目说明，用于解读方法来源。下面的风格适配是本仓库的设计示例，不是原作的风格分类，也不表示已经完成跨模型生成测试。*

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
| 为同一创意切换视觉风格 | [风格适配示例](docs/style-adaptability.md) |
| 了解 Skill 的入口与路由 | [SKILL.md](skill/hell-grind-aigc-skill/SKILL.md) |
| 深入理解提示词与生产结构 | [七层架构](skill/hell-grind-aigc-skill/references/prompt-architecture.md) · [项目 schema](skill/hell-grind-aigc-skill/references/project-schemas.md) |
| 查看方法来源与研究限制 | [方法论证据](skill/hell-grind-aigc-skill/references/methodology-evidence.md) · [来源与许可](NOTICE.md) |
| 查看版本变化或提交改进 | [更新记录](CHANGELOG.md) · [贡献指南](CONTRIBUTING.md) |

## 来源与致谢

本项目受 Higgsfield Studio 公开的 **Hell Grind** 制作资料启发，独立整理出可复用的工作流、模板、检查工具与原创示例。

**[查看 Hell Grind 官方开放项目、影片与制作说明 →](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind)**

本仓库是独立的社区项目，与 Higgsfield Studio 无官方隶属关系。文档中的原作图片通过官方页面所用地址引用，未打包进 Skill，也不是可直接复用的生成素材。原项目材料适用其[官方许可](https://higgsfield.ai/licences/owl-p-nl-1.0)，不适用本仓库的 MIT 许可。详见 [NOTICE](NOTICE.md)。

## 参与贡献

欢迎分享可复现的失败案例、原创提示词示例、客户端接入经验、翻译和文档改进。先看[贡献指南](CONTRIBUTING.md)，再[提交 Issue](https://github.com/renmu2017/Hell-Grind-AIGC-Skill/issues) 或 Pull Request。

如果这套工作流对你有用，欢迎点亮 Star，或把它分享给一起创作的人。

## 许可证

本仓库原创代码、文档、模板与示例采用 [MIT License](LICENSE)。复制或分发时保留版权与许可声明；第三方名称与引用图片的权利边界见 [NOTICE](NOTICE.md)。
