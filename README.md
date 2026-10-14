# 程序化游戏美术（Procedural Game Art）

一个 Agent Skill：**用代码设计、生成和打磨游戏美术** —— 程序化 2D 图形与纹理、3D 模型与场景、
材质、着色器、动画和特效。全部资产由代码产出，不依赖外部图片或模型文件。

适用于制作游戏资产、提升原型画质、修复程序化美术的造型/质感/风格问题。
按现有引擎适配，不绑定某个引擎或某个预制生成器。

## 安装

这是 [DeepSeek Harness](https://github.com/deepseek-ai)（dsh）格式的 Skill，
本质是一组 Markdown 文件，放进 skills 目录即可被发现：

```bash
# 用户级（所有项目生效）
git clone https://github.com/xihoo/procedural-game-art.git \
  ~/.dsh/skills/procedural-game-art

# 项目级（只在某个项目生效）
git clone https://github.com/xihoo/procedural-game-art.git \
  <你的项目>/.dsh/skills/procedural-game-art
```

Windows 上用户级目录是 `%USERPROFILE%\.dsh\skills\`。

装完之后，制作游戏美术的任务里 Agent 会自动看到它；也可以显式说「用 procedural-game-art 来做美术」。

## 内容

```
SKILL.md                        工作边界、制作流程、迭代与交付要求
references/
  2d-art.md                     图标、精灵、背景、程序化纹理
  3d-art.md                     模型、材质、场景与实时表现
  visual-review.md              视觉诊断与迭代（含"现象 → 优先检查"对照表）
  source-lessons.md             精品项目中可迁移的经验（外部案例，带出处）
agents/openai.yaml              技能元数据
```

## 核心主张

- **尊重用户指定的风格、视角和预算**，沿用项目现有的技术与美术语言。
  技术能力不足时先缩小当前实现任务，不擅自把写实改成卡通、把自由移动改成固定镜头。
- **先确定观看条件再动手**：用途和视角、视觉语言、资产接口、约束和验证方式。
  信息足够时直接行动，不额外要求用户填问卷。
- **先建立一个能代表最终效果的样品**（关键资产 + 必要环境 + 实际游戏镜头），
  达到约定目标后再扩展资产家族。
- **不用增加多边形、随机噪声、粒子、Bloom 或文件长度替代设计。**
- **看到截图不等于完成诊断。** 每次有意义的修改都走这条链：
  实际观察 → 原因假设 → 可定位的修改 → 同条件复查 → 保留或回退。
- **交付时区分「代码已实现」「运行已验证」「视觉已检查」**，不把三者混为一谈。
- 本 Skill 不需要图像生成服务或外部资产；也不把多 Agent 当作质量保证。

## 视觉诊断对照表（节选）

`references/visual-review.md` 里有一张排查方向表：

| 现象 | 优先检查 |
| --- | --- |
| 像占位模型 | 轮廓、比例、分件、厚度、观察角度 |
| 所有表面像塑料 | 材质参数、反射环境、光照、曝光、色彩空间 |
| 画面很乱却没有重点 | 明度层次、主体尺寸、装饰分布、特效遮挡 |
| 近看刺眼，远看没细节 | 细节频率、纹理过滤、屏幕覆盖面积 |
| 物体漂浮或纸片感 | 接触、厚度、阴影、法线、比例 |
| 截图不错，运动时很差 | 枢轴、挂点、时间步长、闪烁、动画过渡 |
| 一套资产像来自不同游戏 | 形体语言、色板、比例、材质与细节尺度 |

## 外部案例的出处

`references/source-lessons.md` 整理了四个项目里可迁移的做法，**仅引用链接与结论，
不包含任何上游代码或素材**。本仓库不复制这些项目的代码：

- [bridge-mind/turbo-kart-rally](https://github.com/bridge-mind/turbo-kart-rally) —— 结构化的程序美术、资产语义与缓存
- [mshumer/Claude-of-Duty](https://github.com/mshumer/Claude-of-Duty) —— 诊断错误会抵消制作投入
- [TonyDowney/kindle](https://github.com/TonyDowney/kindle) —— 风格、世界规则与动态表达一致
- 边界案例：[Silent Meridian](https://github.com/stackloomdev/silent-meridian)、[Neural Sight](https://github.com/monstercameron/Neural-Sight) —— 不要误判画质来源

引用链接指向可变分支，实际复用时请记录所用提交，并核对依赖版本与许可证。

## 配套 Skill

**[browser-game-runtime-pitfalls](https://github.com/xihoo/browser-game-dev-pitfalls)** ——
网页游戏开发注意事项与运行时故障排查（抖动、闪烁、物体消失、高刷屏异常、手感发飘、掉帧），
含一个可运行的浏览器诊断探针。

美术做完之后，"动起来对不对"是另一类问题 —— 那份 Skill 管的就是这个。

## 许可证

MIT
