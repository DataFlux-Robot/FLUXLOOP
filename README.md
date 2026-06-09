<div align="center">

# FLUXLOOP

### The engine — and the master plan — for self-researching machines
### 通往「通用机器人 + 通用自主研究能力」的引擎与路线图

<sub>by **DataFLUX Dynamics**</sub>

</div>

---

## The Grand Plan · 宏大计划

想象一台机器人，遇到任何未知问题，它不等人。

电池不够用——它自己研究新的电池配方，做出来，给自己换上。
零件不认识、没有驱动——它自己探测、自己写驱动、把它接进身体。
落到一颗没人去过的星球——它就地取样、研究当地化学、造出工具，自给自足。

**通用机器人 + 通用自主研究能力。** 一台能自己提出假设、设计实验、操作仪器、发现规律、并立刻把成果造出来的机器——这是机器人技术树的终点，也是递归自我改进（recursive self-improvement）的雏形。多数人认为它要到 2040 年才可能。

> A robot that, facing any unknown, doesn't wait for us — it researches, experiments, invents, and upgrades **itself**. General-purpose robots + general-purpose auto-research. The endgame of robotics, and the seed of recursive self-improvement.

**我们认为它可以更早。而且我们已经在一步步搭建通往它的每一块拼图。**

这个计划看起来不可能。但每一个不可能的宏大计划，都是被**分解成可执行的小步骤**之后才变得可能的。下面是我们的 roadmap——以及我们已经走到了哪。

---

## The Roadmap · 路线图

```
 Phase 0          Phase 1            Phase 2             Phase 3              Phase 4
 已造的基石   →   FLUXLOOP      →    自研一个子系统   →   通用物理自主研究  →   递归自我改进
 building       agent-led          auto-research        general physical      recursive
 blocks         hardware R&D       a subsystem          auto-research         self-improvement
 ✅ validated   🏗️ now             🔮 next               🔮 vision             🔮 north star
   │               │                   │                    │                     │
   └─ 真 repo ─────┴── 闭合第一个 ──────┴── 从一个零件 ──────┴── 跨物理场、────────┴── 机器人设计并
      已验证          自主研发闭环          到一台机器人           跨硬件类          制造自己的下一代
```

### Phase 0 — 基石已造并验证 · Building blocks, already built & validated `✅`
不是 PPT，是跑起来、且对标黄金标准验证过的代码。见下方 [Component Map](#component-map--组件地图)。

### Phase 1 — FLUXLOOP：Agent-led 硬件研发 · `🏗️ 进行中`
把基石编排成第一个闭环：给一个文档不全、协议私有的硬件（电机/作动器/传感器），AI 自主探测它 → 多物理场仿真预测 → 自动标定 sim2real → 生成驱动 + 标定真实性能。**把专家几个月的活压成几小时，让 3 人团队的研发吞吐接近 30 人。**
> 这是"自主研究"第一次作用在**一个真实硬件**上。MVP 已验证：Agent 接示波器/继电器、自主查资料、完成驱动开发。

### Phase 2 — 从一个零件，到一台机器人 · `🔮 Next`
auto-research 从"标定一个部件"扩展到"自主设计与改进一个模块化机器人子系统"——驱动 + 供电 + 结构 + 控制协同迭代（FluxTendril + FluxCurrent + FluxWeave + FluxTide）。

### Phase 3 — 通用物理自主研究 · `🔮 Vision`
auto-research 跨越多个物理场（气动 + 电磁 + 热 + 结构）与多类硬件——一个不绑定单一领域的通用物理研究能力。第一性原理求解 + 数据驱动修正项，从方程算精确物理，再用现场实验校正。

### Phase 4 — 递归自我改进 · `🔮 North Star`
机器人用自己的 auto-research 能力，设计并制造自己效率更高的下一代部件，自己换上。**通用机器人 + 通用自主研究能力**在此闭环。

> **诚实声明**：Phase 0 已验证，Phase 1 进行中（电学闭环已通），Phase 2-4 是 roadmap 与北极星。我们不假装已经到达终点——我们证明的是，**我们已经在路上，且每一步都有真实代码落地**。

---

## Component Map · 组件地图

每个 repo 不是孤立项目，而是这条路上的一块拼图：

| 层 Layer | 组件 Component | 角色 Role | 状态 |
|---|---|---|---|
| 🧠 Mind | **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** (EvoScientist) | 自主研究引擎：Claim Chain v2 知识图谱 + PES 流转 + 21 Skills + 4-Persona/ELO/MAP-Elites | ✅ v0.3.0 活跃 |
| 🌐 World | **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | 第一性原理**气动**多物理场求解（GPU 涡方法；Goland 颤振 2.4% 误差，97% Theodorsen 精度） | ✅ 已验证 |
| 🌐 World | **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **电磁/相控阵**多物理场仿真（IQ 级；MATLAB 校验 83/83，~985 组参数扫描） | ✅ 已验证 |
| 🦾 Body | **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | 实时神经系统 + Actuator/Sensor Bridge：协议统一（CAN/EtherCAT/SPI/PWM）、热插拔、硬件 root-of-trust（SE/TPM）、TSN 双域实时控制 | 🏗️ 架构/原型期 |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** | 统一供电与多路母线（GaN），模块化机体的电力底座 | 🏗️ v0 硬件 |
| 🦾 Body | **[FluxTide](https://github.com/DataFlux-Robot/FluxTide)** | 运动控制（MPC + 全身控制 WBC） | 🌱 规划中 |
| 🛠️ Tooling | **[FluxWeave](https://github.com/DataFlux-Robot/FluxWeave)** | 动态 URDF 建模工作台（STL → URDF → USD） | ✅ 可用 |

**三层心智模型**：🧠 Mind（研究大脑，提假设/设计实验/符号回归发现修正项）· 🌐 World（精确物理，第一性原理求解 + 数据修正，**不是**数据驱动的近似世界模型）· 🦾 Body（实体接入，让 Agent 能真实下指令、读传感器、驱动硬件——云端基座模型碰不到的地方）。

---

## Why Now · 为什么是现在

四个条件过去 12 个月才同时跨过门槛，缺一不可：

1. **Agent 第一次能碰硬件** — MCP / Skill 出现前，Agent 与物理硬件是断的。
2. **Agent 第一次能做研究** — auto-research 刚能产出 workshop 级研究产出。
3. **精确物理底座刚开源** — [NVIDIA Newton](https://developer.nvidia.com/newton-physics)（2025）可微分 GPU 力学引擎，直接支撑自动系统辨识。
4. **基座模型刚够强** — 撑得起多步自主研究闭环。

任一个晚一年，这事都做不成。这是早期布局窗口。

---

## Join Us · 一起造

这是一块需要很多人的拼图。无论你是 **real-time 内核 / 嵌入式 / 多物理场仿真 / 机器人控制 / Agent 系统** 的高手，还是被同一个未来吸引的人——欢迎你加入。

- ⭐ **Star** 这个 repo，关注路线图推进
- 🛠️ **贡献**：查看各组件仓库的 Issues 与 Discussions
- 💬 **反馈**：你在硬件研发里被坑过哪些（驱动、协议、sim2real）？告诉我们，这直接影响我们造什么
- 🤝 **投资 / 合作**：DataFLUX Dynamics 正在推进早期布局，欢迎接触

---

## License

各子项目遵循其各自仓库的许可证（多为 Apache-2.0）。

---

<div align="center">
<sub><b>FLUXLOOP</b> · DataFLUX Dynamics<br/>
从一个硬件的自动研发，走向能自我研究、自我进化的机器。<br/>
<i>From auto-researching one piece of hardware, toward machines that research and improve themselves.</i></sub>
</div>
