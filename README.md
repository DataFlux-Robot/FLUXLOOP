<div align="center">

# FLUXLOOP

### Agent-led Hardware R&D · 让硬件研发像写代码一样自动化

**An AI agent that autonomously brings up unknown hardware, characterizes its real physics, and writes the driver — collapsing months of expert work into hours.**

**一个能自主接入未知硬件、标定真实性能、生成驱动的 AI 研究员 —— 把专家几个月的活压成几小时。**

<sub>by **DataFLUX Dynamics**</sub>

</div>

---

## The Problem · 我们要解决的痛

把一个文档不全、协议私有的硬件（电机 / 作动器 / 传感器）接进系统、搞清它的真实性能、写出可用驱动 —— 这件事今天仍然要一个专家手搓几周到几个月。

调一个 Maxon 电机，CiA402 标准我们懂、STM32 库我们手搓，但具体协议排列没文档，只能一遍遍烧程序、改代码 loop 出来 —— 连 Maxon 这种大厂都这样。想找外包？约不到人，少数能干的开价好几万一单。小厂更糟，连自己产品的真实性能都说不清。

> Bringing up an under-documented, private-protocol hardware part — discovering its protocol, characterizing its true performance, and writing a working driver — still costs a specialist weeks to months. Even for premium vendors like Maxon. Outsourcing? The few engineers who can do it are scarce and expensive. Small vendors? They often can't even tell you their own product's real performance.

**FLUXLOOP** 把这件事交给 AI：自主探测硬件 → 多物理场仿真预测 → 自动标定 sim2real → 生成驱动。让一个 3 人团队的硬件研发吞吐，接近过去 30 人团队。

---

## What FLUXLOOP Is · FLUXLOOP 是什么

FLUXLOOP 是 DataFLUX Dynamics 的**总装与编排层** —— 它把我们已经构建的研究引擎、多物理场求解器、实时硬件控制层，编排成一个闭环的 **agent-led 硬件研发系统**：

```
        ┌──────────────────────────────────────────────────────────┐
        │                      FLUXLOOP                            │
        │              Agent-led Hardware R&D Loop                 │
        └──────────────────────────────────────────────────────────┘

   ┌─ 🧠 MIND ──────────┐   ┌─ 🌐 WORLD ──────────┐   ┌─ 🦾 BODY ──────────┐
   │   Flux-Insight     │   │  FLUXVortex (aero)  │   │   FluxTendril      │
   │   (EvoScientist)   │   │  FluxPhased  (EM)   │   │  Actuator/Sensor   │
   │                    │   │                     │   │      Bridge        │
   │ 提假设·设计实验     │   │ 第一性原理多物理场   │   │ 协议探测·驱动生成   │
   │ 符号回归发现修正项  │   │ GPU 加速·精度验证    │   │ 实时安全控制        │
   └─────────┬──────────┘   └──────────┬──────────┘   └─────────┬─────────┘
             │                         │                        │
             └────────── propose ──────┼────── predict ─────────┘
                                       │
                            ┌──────────▼───────────┐
                            │   probe real hardware │
                            │   测量 → 对比 → 修正   │
                            └──────────┬───────────┘
                                       │
                  ┌────────────────────▼────────────────────┐
                  │  driver + real performance model         │
                  │  + proprietary multiphysics data ↺ MIND  │
                  └──────────────────────────────────────────┘
```

**闭环逻辑**：Agent（Flux-Insight）提出假设并设计实验 → 多物理场求解器（FLUXVortex / FluxPhased）预测 → 通过 FluxTendril 探测真实硬件 → 对比仿真与实测、自动标定 sim2real；当调参闭合不了 gap 时，用 auto-research 闭环（查资料 → 实验 → 符号回归发现修正项 → 构成 Claim Chain）**自主补全修正模型**。每一次闭环都沉淀别人没有的多物理场修正数据，回流喂养引擎。

---

## Component Map · 组件地图

每个 repo 不是孤立的项目，而是这条闭环里的一环：

| 层 Layer | 组件 Component | 角色 Role | 状态 Status |
|---|---|---|---|
| 🧠 Mind | **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** (EvoScientist) | 自主研究引擎：Claim Chain v2 知识图谱 + PES 流转 + 21 Skills + 4-Persona/ELO/MAP-Elites | ✅ v0.3.0，活跃 |
| 🌐 World | **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | 第一性原理**气动**多物理场求解（GPU 涡方法，Goland 颤振 2.4% 误差，97% Theodorsen 精度） | ✅ 已验证 |
| 🌐 World | **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **电磁/相控阵**多物理场仿真（IQ 级，MATLAB 校验 83/83） | ✅ 已验证 |
| 🦾 Body | **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | 实时神经系统 + Actuator/Sensor Bridge：协议统一（CAN/EtherCAT/SPI/PWM）、热插拔、硬件 root-of-trust（SE/TPM）、TSN 双域实时控制 | 🏗️ 架构/原型期 |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** | 统一供电与多路母线（GaN），模块化机体的电力底座 | 🏗️ v0 硬件 |
| 🦾 Body | **[FluxTide-MPC-WBC](https://github.com/DataFlux-Robot/FluxTide-MPC-WBC)** | 运动控制（MPC + 全身控制 WBC） | 🌱 规划中 |
| 🛠️ Tooling | **[FluxWeave](https://github.com/DataFlux-Robot/FluxWeave)** | 动态 URDF 建模工作台（STL → URDF → USD），为仿真与建模提供资产 | ✅ 可用 |

---

## Architecture · 三层架构

- **🧠 Mind（研究大脑）** — Flux-Insight / EvoScientist。把"假设 → 实验 → 分析 → 修正"的科研循环变成可运行的 Agent 工作流，Claim Chain 是唯一真相源。
- **🌐 World（精确物理）** — FLUXVortex（气动）+ FluxPhased（电磁）。**第一性原理求解 + 神经网络/符号回归修正项**，不是数据驱动的近似世界模型。这是和通用 world model 路线的根本区别：我们从方程算精确物理，再用现场数据校正。
- **🦾 Body（实体接入）** — FluxTendril（实时安全控制 + 协议探测）+ FluxCurrent（电力）+ FluxTide（运动控制）。让 Agent 能真实地下指令、读传感器、驱动硬件 —— 这是云端基座模型碰不到的地方。

---

## Why Now · 为什么是现在

四个条件过去 12 个月才同时跨过门槛，缺一不可：

1. **Agent 第一次能碰硬件** —— MCP / Skill 出现前，Agent 与物理硬件是断的。
2. **Agent 第一次能做研究** —— auto-research 刚能产出 workshop 级研究产出。
3. **精确物理底座刚开源** —— [NVIDIA Newton](https://developer.nvidia.com/newton-physics)（2025）提供可微分 GPU 力学引擎，直接支撑自动系统辨识。
4. **基座模型刚够强** —— 撑得起多步自主研究闭环。

任一个晚一年，这事都做不成。

---

## Status · 当前状态（诚实分层）

- ✅ **已构建并验证的组件**：Flux-Insight（研究引擎）、FLUXVortex（气动求解，黄金标准验证）、FluxPhased（电磁仿真，MATLAB 验证）、FluxTendril 架构、FluxCurrent v0 硬件。
- 🏗️ **进行中**：FLUXLOOP 端到端编排层、FluxTendril 实物原型。
- 🌱 **路线图**：电学/热学多物理场标定的端到端整合、未知协议自动发现的产品化、安全探测策略、运动控制（FluxTide）。

> 本 README 描述的是**正在成形的整体架构**。各组件已独立验证，端到端的 agent-led 闭环整合仍在推进中。

---

## License

各子项目遵循其各自仓库的许可证（多为 Apache-2.0）。

---

<div align="center">
<sub>FLUXLOOP · DataFLUX Dynamics · Agent-led Hardware R&D</sub>
</div>
