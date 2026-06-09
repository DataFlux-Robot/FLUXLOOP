<div align="center">

# FLUXLOOP

### An AI agent that brings up unknown hardware, discovers its real physics, and writes the driver — on its own.

**Software got agents that write code. Hardware still takes an expert *weeks* to make one undocumented motor talk.**
We're closing that gap — as the first step toward machines that research and improve *themselves*.

<sub>· [中文](#中文) · built by **DataFLUX Dynamics** · 🏗️ early & open ·</sub>

</div>

---

## The idea

Today's AI can write a web app in minutes. Point it at a real motor with a vague datasheet and a private protocol, and it's helpless — because **intelligence still can't touch the physical world.** That last gap is where every robotics team bleeds weeks.

FLUXLOOP is the missing loop:

```
   AGENT proposes  →  SOLVER predicts  →  PROBE the real hardware  →  CALIBRATE sim↔real
        ↑                                                                    │
        └──────────────── driver + real-performance model ←─────────────────┘
                          (+ proprietary correction data, fed back)
```

Give it a black-box actuator/sensor. It probes the protocol, predicts behavior with a first-principles multiphysics solver, runs experiments against the real device, and when parameter-fitting isn't enough it **discovers new correction terms** (symbolic regression) — closing the sim-to-real gap and emitting a working driver. **Months → hours.**

## The bet worth arguing about

> **We think sim2real is a model-*discovery* problem, not a domain-randomization problem.**
> Everyone else learns approximate physics from data (and inherits "physics slop"). We solve precise physics from first principles, then let an agent discover the correction terms that close the gap to reality. First-principles + learned residual > data-driven world model — for anything where physics precision actually matters.
>
> Think we're wrong? [Open an issue and tell us.](https://github.com/DataFlux-Robot/FLUXLOOP/issues)

## Is it real? Yes — here's the code

Not slideware. Working repos, validated against gold standards:

| | What | Proof |
|---|---|---|
| 🧠 **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** | Autonomous research engine (Claim-Chain knowledge graph + 21 composable skills) | v0.3.0, active |
| 🌐 **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | First-principles **aero** solver, GPU vortex method | Goland flutter **2.4% err**, 97% Theodorsen |
| 🌐 **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **EM / phased-array** multiphysics sim (IQ-level) | MATLAB-validated **83/83**, ~985 sweeps |
| 🦾 **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | Real-time nervous system: protocol-unifying Actuator/Sensor Bridge + hardware root-of-trust | architecting |
| 🦾 **[FluxTide](https://github.com/DataFlux-Robot/FluxTide)** | Universal robot controller (sample-based MPC, parallel envs) | usable |
| 🔌 **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** · **[FluxPulse](https://github.com/DataFlux-Robot/FluxPulse)** | Power & bus backbone (GaN; interleaved/bidirectional) | v0 hw |

**MVP, validated:** an agent autonomously read the docs, drove an oscilloscope + relay, and wrote the driver itself.

## The bigger bet — why this is a loop, not a tool

A driver generator is a feature. We're after the loop behind it: **physical auto-research** — an agent that researches the physical world, and eventually improves its own body.

```
 Phase 0 ── Phase 1 ───────── Phase 2 ──────── Phase 3 ──────────── Phase 4
 blocks     FLUXLOOP          a subsystem      general physical     recursive
 ✅ built    🏗️ now            🔮 next           auto-research 🔮      self-improvement 🔮
            (1 hardware)      (1 robot)        (any physics)        (it builds its own next gen)
```

Phase 0 is shipped. Phase 1 is live (electrical loop closed; multiphysics = aero+EM today, thermal next). Phases 2–4 are the north star. **We don't claim we're there — we claim every step has real code under it.** That's the whole point.

## Why now

Four thresholds crossed in the last 12 months, and not before: agents can finally *touch* hardware (MCP/Skill), agents can finally *do research* (workshop-grade output), a differentiable GPU physics base went open ([Newton](https://developer.nvidia.com/newton-physics), 2025), and base models got strong enough for multi-step autonomous loops. A year earlier, none of this works.

## Come build — or come argue

This is a big puzzle and we want sharp people on it.

- ⭐ **Star** if you think physical AI's missing piece is *grounding*, not scale
- 💬 **[Discussions](https://github.com/DataFlux-Robot/FLUXLOOP/discussions)** — argue the sim2real-as-model-discovery thesis, or tell us what black-box hardware wrecked your last month
- 🛠️ Real-time kernels · multiphysics · robot control · agent systems — the component repos have open issues
- 🔬 Researchers/builders who care about recursive self-improvement in the *physical* world: let's talk

---

<a name="中文"></a>

## 中文

**FLUXLOOP：一个能自主接入未知硬件、标定真实物理、生成驱动的 AI 研究员。**

软件已经有了会写代码的 Agent；硬件至今要专家花几周，才能让一个没文档、私有协议的电机"开口"。FLUXLOOP 补上这一环——也是通往"能自我研究、自我进化的机器"的第一步。

- **闭环**：Agent 提假设 → 第一性原理多物理场求解器预测 → 探测真实硬件 → 自动标定 sim2real；调参不够时用符号回归**自主发现修正项** → 输出驱动 + 真实性能模型。**几个月 → 几小时。**
- **值得吵的命题**：sim2real 本质是**模型发现**问题，不是 domain randomization。别人从数据学近似物理（physics slop），我们从方程算精确物理、再让 Agent 发现修正项。物理精度要紧的场景，第一性原理 + 数据残差 > 数据驱动 world model。
- **是真的**：FLUXVortex（Goland 2.4% 误差）、FluxPhased（MATLAB 83/83）、Flux-Insight（v0.3.0）、MVP 已让 Agent 自主写出驱动。
- **诚实**：Phase 0 已验证、Phase 1 进行中（电学闭环已通，多物理场=气动+电磁，热在路上），Phase 2–4 是北极星。不假装到终点——每一步都有真代码。

不同意？[来开个 issue 吵架。](https://github.com/DataFlux-Robot/FLUXLOOP/issues)

---

<div align="center">
<sub><b>FLUXLOOP</b> · DataFLUX Dynamics · early & open<br/>
<i>From auto-researching one piece of hardware, toward machines that research and improve themselves.</i></sub>
</div>
