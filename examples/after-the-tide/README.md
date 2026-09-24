# AFTER THE TIDE — 原创视觉案例 / Original visual study

[中文首页](../../README.md) · [English overview](../../README.en.md) · [来源与许可 / Notice](../../NOTICE.md)

**一个 brief，一张海报，两张概念剧照。** 本案例使用 Hell Grind AIGC Skill 组织新提示词，通过 OpenAI 图像生成工具完成，展示人物约束、参考范围、空间设计与局部修正如何用于实际创作。

**One brief, one poster, two concept stills.** New prompts were developed with Hell Grind AIGC Skill and rendered with OpenAI's image generation tool. This case demonstrates character constraints, scoped references, spatial design, and a targeted correction in practice.

这些是原创 AI 概念图，没有对应的已完成影片。生成时未使用 Hell Grind 原作图像、角色、资产或源提示词；所有图片参考均来自本案例内部。

These are original AI concept images, not frames from a completed film. No Hell Grind imagery, characters, assets, or source prompts were used for generation. Every image reference came from this case itself.

![AFTER THE TIDE concept poster](../../docs/assets/after-the-tide-poster.png)

## Brief 与约束 / Brief and constraints

风暴过后，一位工程师修复海上气象站的信标，等待远方的回应。画面传达疲惫之后的平静与希望，采用写实的近未来电影语言。

After a storm, a lone engineer restores an offshore weather station's beacon and waits for a distant reply. The treatment is grounded near-future cinema, with quiet hope after exhaustion.

| 项目 / Field | 创作决定 / Creative decision |
| --- | --- |
| 模式 / Mode | 图片创作，标准版；海报按版式与精确文字增加约束。 / Standard image creation, with additional layout and exact-text constraints for the poster. |
| 角色 / Character | 恰好一位成年女性工程师，黑色单辫、黄色防水外套、深色工作服。 / Exactly one adult woman engineer, a black braid, saffron rain jacket, dark workwear. |
| 道具 / Prop | 一个胸前圆形铜质信号仪；背面机位中不应移到背后。 / One round copper signal instrument worn on the chest; a rear view must not relocate it onto the back. |
| 世界 / World | 海上环形气象站、栈道、风暴后的海面和琥珀色信标。 / A circular offshore weather station, a causeway, a storm-clearing sea, and an amber beacon. |
| 视觉 / Treatment | 蓝灰与深青环境、黄色服装、琥珀光点；真实湿润材质与细微胶片颗粒。 / Blue-grey and petrol surroundings, saffron clothing, amber light, wet surfaces, fine film grain. |
| 输出 / Deliverables | 横向概念海报一张，环境远景与人物近景各一张；剧照无文字。 / One landscape poster, one environmental still, one close-up; no text in the stills. |

人物年龄、职业、服装、场景与光色是为本案例补充的创作选择，来自新的 brief。没有指定真实演员、既有角色或原作构图。

Age, occupation, wardrobe, setting, and lighting are creative choices for this new brief. No real performer, existing character, or source-film composition was specified.

## 提示词与参考范围 / Prompts and reference scopes

提示词正文按创意目标、主体、空间、摄影、光色材质和交付约束组织，不包含特定模型的参数语法。下面链接保存实际提交的文本，包括海报的第二次局部修正。

The creative prompts describe intent, subject, space, camera, light, materials, and delivery constraints without model-specific parameter syntax. Linked files preserve the text actually submitted, including the second, targeted poster revision.

| 顺序 / Order | 生成记录 / Generation record | 继承 / Inherit | 排除 / Exclude |
| --- | --- | --- | --- |
| 1 | [人物近景 / Close-up](closeup-prompt.md) | 无图片参考；从文字建立人物。 / Text only; establishes the character. | 明确不使用之前对话中的图片。 / No earlier conversation artwork. |
| 2 | [海报初稿 / Poster draft](poster-prompt.md) | 近景中的人物、发型、外套、工作服和胸前仪器。 / Character, hair, wardrobe, and chest instrument from the close-up. | 人物姿态、近景构图、室内空间、光线与背景。 / Pose, close crop, room, light, and background. |
| 3 | [海报局部修正 / Poster correction](poster-prompt.md#revision-2--targeted-continuity-correction) | 海报初稿的文字、构图、人物位置与环境。 / Poster draft's text, layout, character placement, and environment. | 移除错误出现在背后的仪器和背带，以衣料补回。 / Remove the misplaced back instrument and harness; restore jacket fabric. |
| 4 | [环境远景 / Environmental still](wide-prompt.md) | 人物近景提供身份与服装；修订海报提供气象站、栈道和光色。 / Close-up supplies character and wardrobe; corrected poster supplies station, causeway, and palette. | 海报文字、版式、人物站位与机位；室内近景背景。 / Poster typography, layout, placement, camera, and the close-up's interior background. |

首次输出与一次局部修正，共 4 次图像工具调用，保留 3 张最终图片。原始海报候选由修订版替换；修正指令保留在提示词文件中。未进行模型比较、批量选优或外部后期合成。

Four image-tool calls produced three retained images: three initial generations and one targeted edit. The corrected poster replaces its draft; the edit instruction is preserved. No model comparison, batch selection, or external compositing was performed.

## 平台适配 / Platform adapter

| 字段 / Field | 本次实际设置 / Recorded setting |
| --- | --- |
| Generation tool | OpenAI built-in image generation tool, `image_gen.imagegen` |
| Model version / seed | `unspecified` — 工具未返回。 / Not exposed by the tool. |
| Reference input | 首图省略；之后显式传入本案例图片路径。 / Omitted for the first image; explicit paths to this case's images thereafter. |
| Requested format | 横向约 16:9；由自然语言提示指定。 / Landscape, approximately 16:9, requested in natural language. |
| Actual files | PNG, 1672 × 941 each |
| Generation date | 2026-09-24 |

其他工具可沿用创意正文，再按自身接口配置参考图、尺寸与参数。相同提示词不保证逐像素复现。

Other tools can reuse the creative instructions with their own reference, size, and parameter settings. The same prompt does not guarantee an identical image.

图片尺寸、文件大小与 SHA-256 见 [generation-record.json](generation-record.json)。 / Dimensions, file sizes, and SHA-256 hashes are recorded in [generation-record.json](generation-record.json).

## 结果与评审 / Results and review

![Environmental concept still](../../docs/assets/after-the-tide-wide.png)

![Character concept close-up](../../docs/assets/after-the-tide-closeup.png)

| 检查 / Check | 实际观察 / Observation |
| --- | --- |
| 海报信息 / Poster text | 标题与两行辅助文字可读，单一场景和左侧留白成立。 / The title and two supporting text elements are readable; the single-scene layout and left-side negative space hold. |
| 道具位置 / Prop placement | 初稿将胸前仪器移到了人物背后；局部修正后背面只保留外套。 / The draft moved the chest instrument onto the back; the targeted edit restores plain jacket fabric. |
| 共同视觉 / Shared treatment | 黄色外套、黑辫、蓝灰海面和琥珀光形成可辨识的共同设定。 / The saffron jacket, black braid, blue-grey sea, and amber light establish a recognizable shared treatment. |
| 精确连续性 / Exact continuity | 仪器大小与衣服细节存在变化；人物眉部小疤痕并非每图可核验。 / Instrument scale and clothing details vary; the small eyebrow scar is not verifiable in every image. |
| 手部与空间 / Hand and space | 远景用了人物左手扶栏，提示词指定右手；栈道和建筑细节也不是严格的三维重建。 / The wide shot places the left hand on the railing despite the requested right hand; architecture and walkway details are not a locked 3D reconstruction. |
| 使用范围 / Accepted use | 用作概念展示；进入连续叙事制作前需进一步锁定资产状态与左右手接点。 / Accepted as concept artwork; a continuous narrative would require stricter asset states and hand/action continuity. |

**提示词结构检查：近景 95/100，海报 100/100，远景 100/100。** 本地审计器把近景中的“不要使用此前图片作为参考”识别为缺少继承范围的参考提及；实际首次调用没有参考输入，因此记录为本例误报，不改写已提交的提示词。该分数仅反映结构和关键词规则，不能抵消上面的视觉问题，也不表示生成成功率。

**Structural prompt audit: close-up 95/100, poster 100/100, wide 100/100.** The local checker flags the close-up's instruction not to use previous artwork as an unscoped reference. The actual first call supplied no reference, so this is recorded as a false positive without rewriting the submitted prompt. Scores describe structure and keyword rules, not visual accuracy or success rates.

```bash
python3 skill/hell-grind-aigc-skill/scripts/audit_prompt.py \
  examples/after-the-tide/closeup-prompt.md --medium image --json
```

从仓库根目录运行，替换文件名可检查另外两份提示词。 / Run from the repository root; replace the filename to inspect the other prompts.

## 复用方法 / Reuse the method

1. 用自己的故事替换 brief，先固定角色数量、身份、服装与关键道具。 / Replace the brief with your story and lock counts, identity, wardrobe, and key props.
2. 先生成资产参考，再逐镜指定继承和排除范围。 / Establish an asset reference, then scope inheritance separately for each shot.
3. 保留每次实际提交的提示词，按画面问题做局部修正。 / Preserve submitted prompts and target observed defects in revisions.
4. 对照硬约束看图，记录仍未解决的细节，再决定用于概念展示还是继续制作。 / Review images against hard constraints, record remaining differences, and decide whether to accept concept art or continue production.

要切换到手绘、水彩或产品视觉，可参考[风格适配](../../docs/style-adaptability.md)。该页面提供文字设计示例，本案例仅实际生成了写实电影风格。

For hand-drawn, watercolor, or product treatments, see [style adaptability](../../docs/style-adaptability.md). That page contains prompt-design examples; this case rendered only cinematic realism.
