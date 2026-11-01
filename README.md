# 大肥鱼 Live2D 模型 · dafeiyu-live2d

！！注意！！
目前仅为第一版，个人做的第一个live2d模型，有很多缺陷。缺少了张嘴动作，因此大肥鱼张嘴时会很丑，在使用模型时，请关闭张嘴动作或者自己手搓一个。如果觉得符号表情很碍事，可以自行设置符号快捷键

一个可直接被 Live2D Cubism 运行时加载的成品模型（moc3 + 全套配置），带 12 组动作、物理演算与口型同步分组。

> 运行环境：**Cubism 5 运行时**（moc3 v5）。可直接用 Cubism Editor 打开 `.cmo3` 继续编辑，或用任意 Cubism SDK / 查看器加载 `face_change.model3.json`。

![预览](<img width="2560" height="1470" alt="Screenshot 2026-11-01 142334" src="https://github.com/user-attachments/assets/b4dacf80-d881-43f1-82ad-de1d10b7fbab" />
)

---

## 模型信息

| 项目 | 值 |
|---|---|
| 模型名 | 大肥鱼（`face_change`） |
| 画布 | 1024 × 1024 |
| 源文件 | `face_change.cmo3`（Cubism 5 可编辑工程，约 3.4 MB） |
| 运行时数据 | `face_change.moc3`（moc3 v5，约 1.0 MB） |
| 贴图 | `face_change.4096/texture_00.png`（4096 图集，1 页） |
| 参数 | 59 个 |
| 绘制对象 | 24 个 ArtMesh |
| 物理 | `face_change.physics3.json`（头发前后摆 ×2、上衣、手袖、尾巴等 20 组） |
| 表情/显示信息 | `face_change.cdi3.json` |

## 目录说明

```
face_change.model3.json      ← 加载入口（运行时读这个）
face_change.moc3             ← 编译后的模型数据
face_change.cdi3.json        ← 参数/部件/ArtMesh 的显示名称（中文）
face_change.physics3.json    ← 物理演算设置
face_change.4096/            ← 贴图图集
face_change.*.motion3.json   ← 动作（见下）
face_change.cmo3             ← Cubism Editor 工程，用于继续编辑
face_change.can3             ← Cubism 场景/动作集
face_change.psd2live.json    ← 生成记录（图层映射、绑定参数、警告）
```

## 动作列表

| 组名 | 文件 | 说明 |
|---|---|---|
| `Idle` | `idle` / `idleCute` | 待机呼吸（两套） |
| `Blink` | `blink` | 眨眼 |
| `Nod` | `nod` | 点头 |
| `Shake` | `shake` | 摇头 |
| `Crouch` | `crouch` | 下蹲 |
| `WeightShift` | `weightShift` | 重心转移 |
| `Shy` | `shy` | 害羞 |
| `HeadTilt` | `headTilt` | 歪头 |
| `Cheer` | `cheer` | 欢呼 |
| `LegKick` | `legKick` | 踢腿 |
| `Sway` | `sway` | 摇摆 |
| `Talk` | `talk` | **口パク（张嘴/闭嘴循环）** — 3.4 秒，幅度轻微，可循环 |

## 参数分组

- `EyeBlink` → `ParamEyeLOpen` / `ParamEyeROpen`
- `LipSync` → `ParamMouthOpenY`（可直接接音频做口型）
- 其余分组：面部角度、眼球、眉毛、身体、物理（头尾/袖/发）、骨骼（手臂/腿/下蹲/跳跃）

## 怎么用

**在网页 / 查看器里加载**

把整个目录作为静态资源，加载 `face_change.model3.json` 即可。例如 `pixi-live2d-display`：

```js
const model = await PIXI.live2d.Live2DModel.from('face_change.model3.json');
app.stage.addChild(model);
model.motion('Talk');   // 播放张嘴/闭嘴
```

**在 Cubism Editor 里继续编辑**

打开 `face_change.cmo3`。注意动作是运行时格式（`.motion3.json`），要进 Editor 的话在动画面板里「导入动作」。

## 致谢 / 制作流程

立绘拆分与自动绑定：**PSD2Live 3.6.0**（生成 `.cmo3` / `.moc3` / `.physics3.json` / 动作预设）
后期整理与导出：**Live2D Cubism Editor 5.3**

---

## 版权

模型与美术资源版权归作者所有。**未授权请勿商用、二次分发或用于训练模型**；想使用请先联系作者。
Live2D Cubism 相关文件的使用还需遵守 [Live2D 软件许可](https://www.live2d.com/eula/live2d-proprietary-software-license-agreement_cn.html)。
