# 精品项目中可迁移的经验

整理日期：2026-10-15。以下来自原仓库说明和选定源码的检查；制作过程和性能数据属于作者记录，并非本 Skill 复现的基准。链接指向可变分支，实际复用时记录所用提交并核对依赖版本与许可证。此包不包含上游代码或素材。

## Turbo Kart Rally：结构化的程序美术

- [模型与材质](https://github.com/bridge-mind/turbo-kart-rally/blob/main/src/models.js)：几何分件、轮胎纹理、号码贴花、程序环境反射和不同材料响应共同构成车辆。可借鉴资产内部的语义结构与缓存方式，不必继承赛车题材。
- [赛道纹理](https://github.com/bridge-mind/turbo-kart-rally/blob/main/src/track-textures.js)：颗粒、磨损与标线服从道路语义。可借鉴有结构的细节分布，而非均匀随机噪声。
- [资产预览](https://github.com/bridge-mind/turbo-kart-rally/blob/main/dev/models-test.js)：独立展示模型与运动状态。可借鉴先检查资产、再检查游戏镜头的工作方式。
- [架构约定](https://github.com/bridge-mind/turbo-kart-rally/blob/main/ARCHITECTURE.md)：单位、朝向、部件接口与挂点明确。真正有用的是约定一致，不是强制使用相同坐标或多 Agent。

## Claude of Duty：诊断错误会抵消制作投入

- [作者复盘](https://github.com/mshumer/Claude-of-Duty#honest-assessment)：作者记录了手部、人物和材质的局限，以及把反射问题误认为缺少纹理的情况。借鉴因果诊断，不把“全程序化”当作写实质量保证。
- [材质生成器](https://github.com/mshumer/Claude-of-Duty/blob/main/src/materials/generator.js)：程序表面可以生成供材质使用的多种数据。借鉴数据约定，不能照搬通道到不同引擎。
- [固定条件截图](https://github.com/mshumer/Claude-of-Duty/blob/main/tools/baseline.mjs)：隔离状态帮助重复比较。像素对比是回归工具，不是美术评分器。
- [流程反思](https://github.com/mshumer/Claude-of-Duty#process-note)：光照、材质与色调映射有耦合，互不协调的并行修改可能恶化画面。借鉴统一诊断，而非简单增加模型或代理数量。

## KINDLE：风格、世界规则与动态表达一致

- [设计与制作记录](https://github.com/TonyDowney/kindle#the-ideas-it-is-built-on)：小球形世界、地形变化、信标和恢复生机的表现服务同一探索体验。可借鉴美术变化与玩法状态共享数据，而不是叠加无关特效。
- [实现目录](https://github.com/TonyDowney/kindle/tree/HEAD/src/js)：按世界、物体、相机、着色器等组织代码，便于局部调整。单文件发布或零依赖不是此 Skill 的要求。

## 两个边界案例：不要误判画质来源

- [Silent Meridian 美术来源](https://github.com/stackloomdev/silent-meridian/blob/main/docs/ART.md)：主体环境是生成插画，代码增加局部几何与动态。只能借鉴布局、风格和交互分离，不能把整个场景当作纯代码建模成果。
- [Neural Sight 制作说明](https://github.com/monstercameron/Neural-Sight#captured-worlds-generated-presence)：实景高斯泼溅与预生成武器画面共同构成写实外观。不能据此承诺代码能从零生成同等复杂度的可自由编辑网格。

## 使用案例的方法

先明确当前待解决的问题，再选择相关实现阅读。提炼适用条件、必要接口、视觉收益和代价；在当前项目的小样中验证。保持用户题材与风格，不为复用案例把新游戏改造成案例的换皮版本。
