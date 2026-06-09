<p align="center">
  <b>F L U X L O O P</b>
</p>

<p align="center">
  <i>一个能自主接入未知硬件、学懂它的真实物理、并写出驱动的 AI 研究员。</i>
</p>

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-early%20%26%20open-orange">
  <img alt="license" src="https://img.shields.io/badge/license-Apache--2.0-blue">
  <img alt="stage" src="https://img.shields.io/badge/physical%20auto--research-phase%201-8A2BE2">
</p>

<p align="center">
  | <a href="./README.md"><b>English</b></a> | <b>简体中文</b> |
</p>

<p align="center">
  <a href="#-概述">概述</a> • <a href="#-它做什么">它做什么</a> • <a href="#-一个值得讨论的命题">命题</a> • <a href="#-已构建并验证">证据</a> • <a href="#-产品阵容">产品</a> • <a href="#-一起来做">参与</a>
</p>

---

## 📌 概述

今天的 AI 能在几分钟里搭出一个 Web 应用。但把它丢给一个文档含糊、协议私有的真实电机，它就束手无策——因为**智能至今"碰不到"物理世界**。正是这最后一道缝，让每一个机器人和硬件团队悄悄损失掉数周时间。

**FLUXLOOP** 要补上这道缝。它是一个开放的、agent-led 的硬件研发系统：给它任意一个作动器、传感器或设备——哪怕没有文档、协议私有、连厂家自己都说不清性能——FLUXLOOP 自主搞清楚怎么和它通信、标定出它真实的物理行为、并产出一个可用的驱动。专家要花几周才能做完的事（协议接入、sim2real 标定、驱动开发），它压缩到几小时。

整个系统围绕三层组织。**研究大脑**（[Flux-Insight / EvoScientist](https://github.com/ExuberantWitness/Flux-Insight)）负责提假设、设计实验，并在"调参不够用"时通过符号回归**自主发现**新的修正模型。**精确物理世界**（[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex) 管气动、[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-) 管电磁）从第一性原理算精确物理，而不是从数据里学近似。**实时安全躯体**（[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril) + [FluxTide](https://github.com/DataFlux-Robot/FluxTide) + [FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)）让 Agent 能真正去探测、驱动物理硬件——这是云端模型永远够不到的地方。

归根结底，它不是一个工具，而是一个**闭环**：FLUXLOOP 每接入一个设备，都会让它的物理模型更准，再反哺下一个。这个闭环，是通往一个更大目标的第一个具体步骤——**physical auto-research（物理自主研究）**：能自我研究、并最终自我进化的机器。

## 🔧 它做什么

```
   Agent 提假设  →  求解器预测  →  探测真实硬件  →  标定 sim ↔ real
       ↑                                                   │
       └──────────  驱动 + 真实性能模型  ←──────────────────┘
                    （+ 专有修正数据，回流喂养）
```

给 FLUXLOOP 一个黑盒部件。它**探测**总线与协议，用第一性原理多物理场求解器**预测**行为，对真实设备**做实验**，**标定** sim2real 的差距——当调参不足以闭合时，自主发现新的修正项——最后产出可用驱动和一个验证过的性能模型。

对工程师来说，体验很简单：**插上那个未知的东西，几小时后拿回一个驱动，和关于"它到底怎么表现"的真相——不是几个月。**

## 🧠 一个值得讨论的命题

> **我们认为 sim2real 本质上是一个模型*发现*问题，而不是 domain randomization 问题。**
>
> 主流做法从海量数据里学近似物理，也继承了它的"physics slop"。我们反过来：从第一性原理算精确物理，再让 Agent *发现*那些把仿真拉回现实的修正项。在任何物理精度真正要紧的场景，第一性原理 + 学习出的残差，胜过数据驱动的 world model。
>
> 不同意？**[来开个 issue 跟我们吵。](https://github.com/DataFlux-Robot/FLUXLOOP/issues)**

## 🧩 已构建并验证

不是 PPT。每个组件都是跑得起来、且对标黄金标准验证过的仓库：

| 层 | 组件 | 是什么 | 证据 |
|---|---|---|---|
| 🧠 Mind | **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** | 自主研究引擎——Claim-Chain 知识图谱 + 21 个可组合 Skills | v0.3.0，活跃 |
| 🌐 World | **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | 第一性原理**气动**求解器（GPU 涡方法） | Goland 颤振 **2.4% 误差**，97% Theodorsen |
| 🌐 World | **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **电磁 / 相控阵**多物理场仿真（IQ 级） | MATLAB 校验 **83/83**，~985 组扫描 |
| 🦾 Body | **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | 实时神经系统：协议统一的 Actuator/Sensor Bridge + 硬件 root-of-trust | 架构中 |
| 🦾 Body | **[FluxTide](https://github.com/DataFlux-Robot/FluxTide)** | 通用机器人控制器——采样式 MPC + 并行环境 | 可用 |
| 🦾 Body | **[FluxAxon](https://github.com/DataFlux-Robot/FluxAxon)** | TSN-over-USB 确定性桥——把主机接入 DataFlux 神经系统 | 🌱 早期 |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** · **[FluxPulse](https://github.com/DataFlux-Robot/FluxPulse)** | 供电与母线底座（GaN；交错式 / 双向） | v0 硬件 |

> **已验证的 MVP**：一个 Agent 自主读文档、驱动示波器 + 继电器、自己写出了驱动。

## 🎁 产品阵容

*我们的 roadmap，实体化——每一档既是能拿在手里的产品，也是通往 2040 愿景的一级台阶。*

每一档都跑同一个 **FLUXLOOP 大脑**（auto-research agent + 物理仿真）。变的是 **Agent 能感知和行动到什么程度**——阶梯从「读传感器」→「看硬件」→「移动着看」→「动手操作」→「设计它」逐级爬升。盒子负责实时控制与感知；重推理和多物理场仿真默认在云端运行（或用本地 AI 模块全本地跑）。

| 档位 | 增加什么 | 适合谁 | 起价 |
|---|---|---|---|
| 🎟️ **软件 / 早期访问** | Agent + 云，无硬件 | 试用、加入社区、给反馈 | ¥199 / $28 |
| ⚡ **MICRO** | 板载初始性能算力 + 云 API | maker、学生、价格敏感开发者（推理走云） | ¥1,999 / $280 |
| 📦 **mini** | 板载中等性能边缘算力 | 已能通过传感器读到状态的硬件 | ¥5,999 / $845 |
| 📷 **pro** | + 固定摄像头 · 多模态 | **无可读状态传感器**的硬件——摄像头成为虚拟传感器 | ¥6,999 / $985 |
| 🦾 **max** | + 可动臂摄像头 + 可调底座（类 [Kynooe](https://www.kynooe.com/)） | **主动感知**——Agent 换位置看被遮挡的状态 | ¥15,999 / $2,250 |
| 🔧 **本地 AI 模块** *(选配)* | 板载高性能算力——本地跑 LLM **和**多物理场仿真 | **数据不出端**的安全部署 | +¥5,999 / +$845 |
| 🔮 **ultra / Ulti** | 模块化人形 → 自动设计模块 | 2040 愿景——**不发售**，仅 notify-me | — |

> *指示性早鸟价——最终档位、目标金额、发货与 demo 随众筹一起公布。`ultra` 和 `Ulti` 是我们奔赴的愿景，明确标注、绝不在真东西之前预售。*

### ☁️ 云与定价 — 公道设计

默认盒子负责控制与感知，**重 LLM 推理和 GPU 多物理场仿真在云端跑**。我们的定价哲学很简单：**你按量付近成本价，我们靠增加的价值赚钱——不在你的 token 上加价。**

- **LLM** —— 按量使用，**比官方 API 价贵 3%**
- **GPU 算力（多物理场仿真）** —— **按市场价**

想自托管？随你，开源的。需要全部本地以满足安全？**本地 AI 模块**让整个闭环跑在你自己硬件上，**数据零出端**。

## ✅ 当前状态 — 诚实说

Phase 0 已交付。Phase 1 进行中：**电学闭环已通**（Agent → 探测 → 驱动），多物理场目前覆盖**气动 + 电磁**（热在路上）。端到端整合、以及未知协议自动发现的产品化，正在开发。Phase 2–4 是北极星。

**我们不假装已经到达终点。我们声明的是——每一步下面都有真实代码，而且我们把它亮出来。** 这就是全部的重点。

## ⏱️ 为什么是现在

四个门槛在过去 12 个月才同时跨过，缺一不可：Agent 第一次能*碰*硬件（MCP / Skill）；Agent 第一次能*做研究*（workshop 级产出）；可微分 GPU 物理底座开源（[NVIDIA Newton](https://developer.nvidia.com/newton-physics)，2025）；基座模型强到能撑起多步自主闭环。早一年，这事做不成。这是早期窗口。

## 🤝 一起来做

这是一块需要很多人的拼图，我们想要锋利的人加入。

- ⭐ 如果你也认为 physical AI 缺的是**接地（grounding）**而不是规模，**Star** 一下。
- 💬 **[Discussions](https://github.com/DataFlux-Robot/FLUXLOOP/discussions)** —— 来辩"sim2real 是模型发现"这个命题，或者告诉我们哪个黑盒硬件毁了你上个月。
- 🛠️ **贡献** —— 实时内核、多物理场、机器人控制、Agent 系统，各组件仓库都有 open issues。
- 🎁 **众筹（即将开始）** —— `软件`、`MICRO`、`mini` 和 `pro`（见[产品阵容](#-产品阵容)）最先上早期支持者计划。*（回报档位、价格、发货随上线公布——Watch 本仓库，第一时间通知。）*

## 📬 联系我们

**对一起开发、讨论想法、或投资感兴趣？** 欢迎联系。

<p align="center">
  <img src="./assets/wechat-qr.png" alt="微信" width="240"/><br/>
  <sub>扫码加微信，备注"FLUXLOOP投资 / FLUXLOOP开发 / FLUXLOOP讨论"</sub>
</p>

更喜欢 GitHub？开个 [issue](https://github.com/DataFlux-Robot/FLUXLOOP/issues) 或 [discussion](https://github.com/DataFlux-Robot/FLUXLOOP/discussions)。

---

<p align="center">
  <sub><b>FLUXLOOP</b> · 由 <b>DataFLUX Dynamics</b> 打造 · early & open<br/>
  <i>从自动研发一个硬件，走向能自我研究、自我进化的机器。</i></sub>
</p>
