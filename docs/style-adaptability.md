# 风格适配 / Style adaptability

[中文首页](../README.md) · [English overview](../README.en.md) · [使用指南 / Usage](usage.md)

**先锁定这幅画面要表达什么，再选择它如何呈现。** 下面用同一个原创场景展示风格适配，便于看清哪些信息保持、哪些信息改变。

**Lock the intent, then choose its visual treatment.** The same original scene appears below in several styles so you can see what stays fixed and what changes.

本页是提示词设计示例，未调用生成模型，不构成跨模型画质、连续性或成功率测试。实际生成的原创写实案例及提示词见 [AFTER THE TIDE](../examples/after-the-tide/README.md)。

This page contains prompt-design examples, not generated results or cross-model quality, continuity, or success-rate tests. For an original generated case in cinematic realism, see [AFTER THE TIDE](../examples/after-the-tide/README.md).

## 共同约束 / Shared contract

```text
主体：恰好一位成年修表师，穿深蓝围裙；工作台上只有一只黄铜怀表和一把镊子。
空间：人物在屏幕左侧，窗户在屏幕右侧，窗光从右向左。
叙事：修表师暂时停下工作，被窗外的光吸引。
视频：6 秒，一个连续镜头，无对白。
节拍：0–2 秒放下镊子；2–4 秒看向窗外；4–6 秒保持视线并轻轻呼气。
摄影机：胸口高度的中景，缓慢直线推进，结束于保留窗框边缘的侧脸近景。
声音：钟表滴答与轻微衣料声，无配乐。
```

```text
Subject: exactly one adult watchmaker in a navy apron;
         one brass pocket watch and one pair of tweezers on the workbench.
Space: character at frame-left, window at frame-right, light traveling right to left.
Intent: a pause in the work as the watchmaker notices the light outside.
Video: 6 seconds, one continuous take, no dialogue.
Beats: 0–2s set down the tweezers; 2–4s look outside;
       4–6s hold the gaze and exhale gently.
Camera: slow straight push from chest-height medium shot to a profile close-up
        retaining the edge of the window frame.
Sound: ticking clocks and a soft fabric rustle; no music.
```

## 风格层写法 / Visual treatments

在共同约束后选用一种风格层。以下描述不应全部混在同一条提示词中。

Choose one treatment to accompany the shared contract. Do not combine all of them into one prompt.

| 方向 / Direction | 可使用的风格层 / Example treatment |
| --- | --- |
| **写实剧情 / Live-action realism** | 清晨柔光，保留皮肤细节、黄铜细划痕与围裙织纹；动作幅度小，表演通过视线和呼吸变化呈现。 / Soft dawn light; retain skin detail, fine brass scratches, and apron weave. Keep gestures small and carry the performance through eyelines and breath. |
| **二维动画 / 2D animation** | 清晰轮廓与有限色块，深蓝围裙保持同一剪影；手部动作先预备再落定，背景纹理跨帧稳定。 / Clean contours and a limited palette; keep the navy apron silhouette consistent. Give the hand action a clear anticipation and settle, with stable background texture. |
| **水彩绘本 / Watercolor illustration** | 暖米色纸底与柔和蓝灰，颜色在边缘轻微晕开；脸、手、怀表保持清楚，纸面颗粒不逐帧翻滚。 / Warm cream paper and soft blue-gray washes, with gentle pigment bleed at the edges. Keep the face, hands, and watch legible; avoid unstable paper texture between frames. |
| **定格模型 / Stop-motion look** | 哑光手工模型、轻微不规则表面与可见织物纹理；姿态有清楚的停顿和落点，保持怀表尺寸。 / Matte handmade models, subtle surface irregularity, and visible fabric texture. Use deliberate pose holds and settles while retaining the watch's dimensions. |
| **科幻 / Science fiction** | 在怀表表面加入低亮青色刻度光，右侧窗光仍是主光；发光只影响附近黄铜与指尖，不增加悬浮道具。 / Add a dim cyan dial glow to the watch while keeping the right-side window as the key light. Let the glow affect nearby brass and fingertips without adding floating props. |

这里的科幻版本需要用户允许改变怀表外观；若外观已获批准且不可修改，就保留原设计，只调整环境色彩。风格要求不会覆盖已批准的产品或角色身份。

The science-fiction treatment assumes permission to change the watch's appearance. If its design is already approved and fixed, preserve it and adapt only the surrounding palette. Style does not override approved product or character identity.

## 产品广告如何迁移 / Applying the workflow to advertising

如果目标改为“展示怀表的工艺”，这是叙事目标变化，应该重新确认镜头重点，而不是只替换风格词。产品广告可以沿用资产、参考范围、镜头起止、材质和验收方法，把检查重点移到表盘文字、指针数量、产品比例和品牌色。

If the goal becomes “show the watch's craftsmanship,” the narrative intent has changed. Reconsider shot emphasis before changing style words. The same asset, reference-scope, camera, material, and review methods apply, with checks focused on dial text, hand count, proportions, and brand colors.

## 怎样检查适配结果 / How to review an adaptation

1. **先查不变量。** 主体数量、身份、左右、道具、时长和对白是否保持？ / Check counts, identity, screen direction, props, duration, and dialogue first.
2. **再查风格是否自洽。** 手绘画面是否还混入了无关的皮肤毛孔、真实快门或照片锐化要求？ / Check that the treatment is coherent; remove incompatible skin, shutter, or photographic sharpening requirements from a drawn style.
3. **最后查动态。** 轮廓、纹理、运动节奏与相邻镜头能否衔接？ / Review contours, texture stability, motion timing, and adjacent-shot handoffs.

平台参数仍然单独记录。提示词结构检查通过后，选择代表性镜头做实际生成，并记录失败、修改变量与复测结果。

Keep provider settings separate. After structural review, generate a representative shot and record failures, changed variables, and retest results.
