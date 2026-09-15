<div align="center">

# 🌌 NEON TETRIS

**现代俄罗斯方块 · 单文件 · 零依赖**

SRS 墙踢 · 7-Bag · Hold · Ghost · T-Spin · Perfect Clear · 全程序化合成器音景

*A single-file, zero-dependency modern Tetris — neon aesthetics, guideline-style rules, and a fully procedural Web Audio soundscape. Open `index.html` and play.*

[![version](https://img.shields.io/badge/version-1.2-00e5ff)]()
[![tech](https://img.shields.io/badge/tech-vanilla%20JS%20%7C%20Canvas%20%7C%20WebAudio-ff2bd6)]()
[![dependencies](https://img.shields.io/badge/dependencies-0-6dff9b)]()
[![size](https://img.shields.io/badge/size-single%20file-ffd60a)]()

</div>

---

## ✨ 特性

### 🎮 现代规则

| 机制 | 说明 |
| --- | --- |
| **SRS 旋转** | 完整 Super Rotation System：J/L/S/T/Z 五踢表 + I 特殊表，CCW 表由 CW 推导 |
| **随机器** | 4 种可切换：**7-Bag**（默认）、**4-Bag**、**Classic** 纯随机、**Random9G**（9 格袋，J/L/T 各 ×2） |
| **Hold** | 一次暂存一个，交换后锁定至当前块落定 |
| **Ghost** | 半透明幽灵块显示落点 |
| **Lock Delay** | 500 ms（可切 0 即时）；移动 / 旋转重置，单块最多 15 次 |
| **DAS / ARR** | 三档：标准 160/45 ms · 快 110/35 ms · 关 |
| **T-Spin** | 3-corner 判定，区分 Mini / Full，last-kick 自动升 Full |
| **Combo** | 连续消行加成 +50 × 连击数 × 等级 |
| **Perfect Clear** | 消行后整盘清空：+2000（Tetris +4000）× 等级 |
| **Next 队列** | 4 格预览 |
| **等级 / 重力** | 每 10 行升 1 级，21 段重力曲线（Lv1 800 ms → Lv20+ 100 ms） |

### 🎨 视觉

- 霓虹发光方块：渐变 + 高光 + 辉光描边
- 消行白闪 + 霓虹扫描线 + 粒子爆发
- 硬降 / 消行 / Tetris 屏幕震动
- 玻璃拟态面板、星点背景、VU 律动条
- 自适应缩放，桌面 / 手机通吃
- 触屏支持：虚拟按键 + 棋盘手势（点按旋转、左右滑移动、下滑软降、上滑旋转）

### 🔊 音频（100% 程序化，零音频文件）

**总线架构**：`voice → dry / 卷积混响 / 反馈延迟 → 压缩限幅 → 输出`

- **卷积混响**：3.2 s 程序化冲激响应（18 ms 预延迟 + 稀疏早期反射，"玻璃房"质感）
- **立体声反馈延迟**：0.315 s，低通 2.4 kHz，反馈 0.42
- **音色**：FM 铃音、滑音振荡器、滤波噪声爆发（硬降冲击、Tetris 镲片、Perfect Clear 类人声合唱）
- **生成式音乐**：Am – F – C – G 循环，前瞻式调度器（25 ms tick / 220 ms lookahead），声部随等级层层展开：

| 等级 | 新增声部 |
| --- | --- |
| Lv1 | Pad 铺底（双 detuned saw + 次八度正弦）+ 贝斯脉冲 |
| Lv3 | 琶音 |
| Lv4 | 加密贝斯（加拍） |
| Lv5 | Hi-hat 微节奏 |
| Lv6 | 高音风铃旋律 |
| Combo ≥ 3 | Shimmer 叠加层 |

BPM 随等级 72 → 106。

## 🕹️ 操作

| 按键 | 功能 |
| --- | --- |
| ← / → | 移动（长按触发 DAS 滑动） |
| ↓ | 软降（长按加速，+1 分/格） |
| Space | 硬降（+2 分/格） |
| ↑ / X | 顺时针旋转 |
| Z | 逆时针旋转 |
| C / Shift | Hold |
| P | 暂停 / 继续 |
| Enter | 开始 / 重新开始 |
| R | 结束后重新开始 |

触屏设备自动显示虚拟按键；也可直接在棋盘上手势操作。

## 🏆 计分

| 项目 | 分数 |
| --- | --- |
| 消 1 / 2 / 3 行 | 100 / 300 / 500 × 等级 |
| Tetris（4 行） | 800 × 等级 |
| T-Spin（无消行） | 400 × 等级（Mini 100） |
| T-Spin 1 / 2 / 3 行 | 基础消行分 + 800 / 1200 / 1600 × 等级（Mini 为 100 + 200×行数） |
| Combo（≥2） | +50 × 连击数 × 等级 |
| Perfect Clear | +2000 × 等级（Tetris 时 +4000） |
| 软降 / 硬降 | +1 / +2 分每格 |

最高分自动存入 `localStorage`。

## ⚙️ 局内设置

- **随机器**：7-Bag / 4-Bag / Classic / Random9G
- **锁定时**：0.5 s / 0 s 即时
- **DAS**：标准 / 快 / 关
- **音乐**：开 / 关；另有全局静音按钮

## 🚀 运行

零构建、零依赖，任选其一：

```bash
# 方式 1：直接打开
open index.html        # macOS
start index.html       # Windows

# 方式 2：本地静态服务器
python3 -m http.server 8000
# → http://localhost:8000
```

或者在仓库 **Settings → Pages** 中选择 `main` 分支 / 根目录，部署 GitHub Pages 在线游玩。

## 📁 项目结构

```
neon-tetris/
├── index.html   # 全部代码：HTML + CSS + 原生 JS（单文件）
└── README.md
```

`index.html` 内部模块：

1. **音频引擎** — 卷积混响 / 延迟 / 压缩总线，voice / FM bell / noise 三类发声原语
2. **音乐调度器** — 前瞻式 step sequencer，等级驱动声部解锁
3. **游戏核心** — SRS 状态表、墙踢、随机器、锁定延迟、T-Spin / Combo / PC 判定
4. **渲染** — Canvas 2D：棋盘、幽灵块、消行动画、粒子、震屏
5. **输入 / UI** — 键盘 DAS、触屏手势、遮罩、自适应缩放

## 📝 备注

- 当前版本（v1.2）为无尽模式；暂未包含 B2B 与 Sprint / Ultra 计时模式
- 界面语言：中文
- 兼容现代浏览器（Chrome / Edge / Firefox / Safari）

</div>
