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

<details open>
<summary><b>🇨🇳 中文</b></summary>

### ✨ 特性

#### 🎮 现代规则

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

#### 🎨 视觉

- 霓虹发光方块：渐变 + 高光 + 辉光描边
- 消行白闪 + 霓虹扫描线 + 粒子爆发
- 硬降 / 消行 / Tetris 屏幕震动
- 玻璃拟态面板、星点背景、VU 律动条
- 自适应缩放，桌面 / 手机通吃
- 触屏支持：虚拟按键 + 棋盘手势（点按旋转、左右滑移动、下滑软降、上滑旋转）

#### 🔊 音频（100% 程序化，零音频文件）

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

### 🕹️ 操作

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

### 🏆 计分

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

### ⚙️ 局内设置

- **随机器**：7-Bag / 4-Bag / Classic / Random9G
- **锁定时**：0.5 s / 0 s 即时
- **DAS**：标准 / 快 / 关
- **音乐**：开 / 关；另有全局静音按钮

### 🚀 运行

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

### 📁 项目结构

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

### 📝 备注

- 当前版本（v1.2）为无尽模式；暂未包含 B2B 与 Sprint / Ultra 计时模式
- 界面语言：中文
- 兼容现代浏览器（Chrome / Edge / Firefox / Safari）

</details>

<details>
<summary><b>🇬🇧 English</b></summary>

### ✨ Features

#### 🎮 Modern rules

| Mechanic | Description |
| --- | --- |
| **SRS rotation** | Full Super Rotation System: 5-kick tables for J/L/S/T/Z + special I table; CCW tables derived from CW |
| **Randomizer** | 4 switchable: **7-Bag** (default), **4-Bag**, **Classic** pure random, **Random9G** (9-piece bag, J/L/T ×2) |
| **Hold** | Store one piece; locked until the current piece lands |
| **Ghost** | Translucent ghost piece shows the landing position |
| **Lock delay** | 500 ms (switchable to instant); resets on move/rotate, max 15 per piece |
| **DAS / ARR** | 3 presets: Normal 160/45 ms · Fast 110/35 ms · Off |
| **T-Spin** | 3-corner rule, Mini / Full, last-kick auto-promotes to Full |
| **Combo** | +50 × combo × level for consecutive line clears |
| **Perfect Clear** | +2000 (Tetris +4000) × level when the field is emptied |
| **Next queue** | 4 previews |
| **Level / gravity** | Level up every 10 lines, 21-step gravity curve (Lv1 800 ms → Lv20+ 100 ms) |

#### 🎨 Visuals

- Glowing neon blocks: gradient + highlight + glow outline
- Line-clear white flash + neon scanline + particle bursts
- Screen shake on hard drop / clears / Tetris
- Glassmorphism panels, starfield background, VU meter
- Responsive scaling for desktop and mobile
- Touch support: on-screen keys + board gestures (tap to rotate, swipe left/right to move, swipe down to soft drop, swipe up to rotate)

#### 🔊 Audio (100% procedural, zero audio files)

**Bus architecture**: `voice → dry / convolution reverb / feedback delay → compressor/limiter → output`

- **Convolution reverb**: 3.2 s procedural impulse response (18 ms pre-delay + sparse early reflections, "glass room" character)
- **Stereo feedback delay**: 0.315 s, 2.4 kHz lowpass, 0.42 feedback
- **Timbres**: FM bells, gliding oscillators, filtered noise bursts (hard-drop impact, Tetris cymbal, choir-like perfect clear)
- **Generative music**: Am – F – C – G loop, lookahead scheduler (25 ms tick / 220 ms lookahead), layers unlock as you level up:

| Level | New layer |
| --- | --- |
| Lv1 | Pad (dual detuned saws + sub sine) + bass pulse |
| Lv3 | Arpeggio |
| Lv4 | Denser bass (extra hits) |
| Lv5 | Hi-hat micro-rhythm |
| Lv6 | High chime melody |
| Combo ≥ 3 | Shimmer layer |

BPM scales with level: 72 → 106.

### 🕹️ Controls

| Key | Action |
| --- | --- |
| ← / → | Move (hold for DAS slide) |
| ↓ | Soft drop (hold to accelerate, +1 pt/cell) |
| Space | Hard drop (+2 pts/cell) |
| ↑ / X | Rotate clockwise |
| Z | Rotate counter-clockwise |
| C / Shift | Hold |
| P | Pause / resume |
| Enter | Start / restart |
| R | Restart after game over |

Touch devices get on-screen keys automatically; you can also gesture directly on the board.

### 🏆 Scoring

| Item | Score |
| --- | --- |
| 1 / 2 / 3 lines | 100 / 300 / 500 × level |
| Tetris (4 lines) | 800 × level |
| T-Spin (no lines) | 400 × level (Mini 100) |
| T-Spin 1 / 2 / 3 lines | base line score + 800 / 1200 / 1600 × level (Mini: 100 + 200×lines) |
| Combo (≥2) | +50 × combo × level |
| Perfect Clear | +2000 × level (+4000 for Tetris) |
| Soft / hard drop | +1 / +2 per cell |

High score is saved to `localStorage`.

### ⚙️ In-game settings

- **Randomizer**: 7-Bag / 4-Bag / Classic / Random9G
- **Lock delay**: 0.5 s / instant
- **DAS**: Normal / Fast / Off
- **Music**: on / off; plus a global mute button

### 🚀 Run it

Zero build, zero dependencies — pick any:

```bash
# Option 1: just open it
open index.html        # macOS
start index.html       # Windows

# Option 2: local static server
python3 -m http.server 8000
# → http://localhost:8000
```

Or enable **GitHub Pages** (Settings → Pages → branch `main` / root) to play it online.

### 📁 Project structure

```
neon-tetris/
├── index.html   # everything: HTML + CSS + vanilla JS (single file)
└── README.md
```

Modules inside `index.html`:

1. **Audio engine** — reverb / delay / compressor bus; voice / FM bell / noise primitives
2. **Music scheduler** — lookahead step sequencer, level-driven layer unlocks
3. **Game core** — SRS state tables, kicks, randomizers, lock delay, T-Spin / Combo / PC detection
4. **Rendering** — Canvas 2D: board, ghost, clear animation, particles, screen shake
5. **Input / UI** — keyboard DAS, touch gestures, overlays, responsive scaling

### 📝 Notes

- Current version (v1.2) is endless mode; B2B and Sprint / Ultra timed modes are not included yet
- UI language: Chinese
- Works in modern browsers (Chrome / Edge / Firefox / Safari)

</details>
