<p align="center">
  <b>F L U X L O O P</b>
</p>

<p align="center">
  <i>An AI agent that brings up unknown hardware, learns its real physics, and writes the driver — on its own.</i>
</p>

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-early%20%26%20open-orange">
  <img alt="license" src="https://img.shields.io/badge/license-Apache--2.0-blue">
  <img alt="stage" src="https://img.shields.io/badge/physical%20auto--research-phase%201-8A2BE2">
</p>

<p align="center">
  | <b>English</b> | <a href="./README_CN.md"><b>简体中文</b></a> |
</p>

<p align="center">
  <a href="#-overview">Overview</a> • <a href="#-what-fluxloop-does">What it does</a> • <a href="#-the-thesis-worth-debating">The thesis</a> • <a href="#-built--validated">Proof</a> • <a href="#-product-lineup">Products</a> • <a href="#-get-involved">Get involved</a>
</p>

---

## 📌 Overview

Today's AI can scaffold a web app in minutes. Point it at a real motor with a vague datasheet and a private protocol, and it's helpless — because intelligence still cannot *touch* the physical world. That last gap is where every robotics and hardware team quietly loses weeks.

**FLUXLOOP** closes it. It is an open, agent-led hardware-R&D system: connect any actuator, sensor, or device — even one with no documentation, an undocumented protocol, and performance specs its own maker can't give you — and FLUXLOOP autonomously figures out how to talk to it, characterizes its true physical behavior, and produces a working driver. What costs a specialist weeks — protocol bring-up, sim-to-real calibration, driver development — it compresses into hours.

The system is organized around three layers. A **research brain** ([Flux-Insight / EvoScientist](https://github.com/ExuberantWitness/Flux-Insight)) proposes hypotheses, designs experiments, and — when parameter-tuning isn't enough — *discovers* new correction models via symbolic regression. A **precise multiphysics world** ([FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex) for aerodynamics, [FluxPhased](https://github.com/ExuberantWitness/FluxPhased-) for electromagnetics) predicts behavior from first principles rather than from data-driven approximation. And a **real-time, secure body** ([FluxTendril](https://github.com/DataFlux-Robot/FluxTendril) + [FluxTide](https://github.com/DataFlux-Robot/FluxTide) + [FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)) lets the agent actually probe and drive physical hardware — the one place a cloud model can never reach.

It is, in the end, not a tool but a **loop**: every device FLUXLOOP touches sharpens its physics models and feeds the next one. That loop is the first concrete step toward a much larger goal — *physical auto-research*: machines that research, and eventually improve, themselves.

## 🔧 What FLUXLOOP does

```
   AGENT proposes  →  SOLVER predicts  →  PROBE the real hardware  →  CALIBRATE sim ↔ real
        ↑                                                                       │
        └──────────────────  driver + real-performance model  ←────────────────┘
                              (+ proprietary correction data, fed back)
```

Give FLUXLOOP a black-box part. It **probes** the bus and protocol, **predicts** behavior with a first-principles multiphysics solver, **runs experiments** against the real device, and **calibrates** the sim-to-real gap — discovering new correction terms when fitting parameters isn't enough — then emits a working driver and a validated performance model.

For the engineer, the experience is simple: *plug in the unknown thing, get back a driver and the truth about how it actually behaves — in hours, not months.*

## 🧠 The thesis worth debating

> **We believe sim2real is a model-*discovery* problem, not a domain-randomization problem.**
>
> The mainstream approach learns approximate physics from massive data — and inherits its "physics slop." We do the opposite: solve precise physics from first principles, then let an agent *discover* the correction terms that close the gap to reality. For anything where physical precision actually matters, first-principles + a learned residual beats a data-driven world model.
>
> Think we're wrong? **[Open an issue and argue with us.](https://github.com/DataFlux-Robot/FLUXLOOP/issues)**

## 🧩 Built & validated

This is not slideware. Each component is a working repo, validated against gold standards:

| Layer | Component | What it is | Proof |
|---|---|---|---|
| 🧠 Mind | **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** | Autonomous research engine — Claim-Chain knowledge graph + 21 composable skills | v0.3.0, active |
| 🌐 World | **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | First-principles **aerodynamics** solver (GPU vortex method) | Goland flutter **2.4% err**, 97% Theodorsen |
| 🌐 World | **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **EM / phased-array** multiphysics sim (IQ-level) | MATLAB-validated **83/83**, ~985 sweeps |
| 🦾 Body | **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | Real-time nervous system: protocol-unifying Actuator/Sensor Bridge + hardware root-of-trust | architecting |
| 🦾 Body | **[FluxTide](https://github.com/DataFlux-Robot/FluxTide)** | Universal robot controller — sample-based MPC + parallel envs | usable |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** · **[FluxPulse](https://github.com/DataFlux-Robot/FluxPulse)** | Power & bus backbone (GaN; interleaved / bidirectional) | v0 hardware |

> **Validated MVP:** an agent autonomously read the docs, drove an oscilloscope + relay, and wrote the driver itself.

## 🎁 Product Lineup

*Our roadmap, made tangible — every tier is both a product you can hold and a step toward the 2040 vision.*

Each tier runs the same **FLUXLOOP brain** (auto-research agent + physics simulator). What changes is **how much the agent can perceive and act** — the ladder climbs from *reading* a sensor → *seeing* the hardware → *moving to see it* → *acting on it* → *designing it*.

| Tier | What's added | The problem it unlocks | Status |
|---|---|---|---|
| **mini** | FLUXLOOP box · single-modal LLM | Hardware that already exposes its working state through readable sensors (encoders, accessible telemetry) | 🎯 crowdfunding |
| **pro** | + fixed external camera · multimodal LLM | Hardware with **no accessible state sensor** (e.g. an actuator without position feedback) — the camera becomes a virtual sensor and the agent *sees* the state | 🎯 crowdfunding |
| **max** | + posable robotic camera arm + adjustable base (à la [Kynooe](https://www.kynooe.com/)) | When one fixed view isn't enough — **active perception**: the agent repositions to observe occluded states from multiple angles | 🔮 stretch |
| **ultra** | + modular humanoid robot | The agent can now **act on and manipulate** hardware, not just observe — and the robot itself becomes a subject of auto-research | 🔮 future |
| **Ulti** | + automated module-design system | The system **designs the humanoid's own modules** → an evolvable, general-purpose humanoid with general research capability. The 2040 endgame. | 🔮 north star · not for sale |

> **This ladder is our roadmap, made tangible.** `mini` & `pro` are the products we bring to crowdfunding first; `ultra` & `Ulti` are the vision we build toward — clearly marked, never sold ahead of what's real. *(Prices, funding target, shipping windows and demos land with the campaign — see [Get involved](#-get-involved).)*

## ✅ Status — honest

Phase 0 is shipped. Phase 1 is live: the **electrical loop is closed** (agent → probe → driver), and our multiphysics today covers **aerodynamics + electromagnetics** (thermal is next). End-to-end integration and the unknown-protocol auto-discovery product are in active development. Phases 2–4 are the north star.

**We don't claim we're there. We claim every step has real code under it — and we show it.** That's the whole point.

## ⏱️ Why now

Four thresholds were crossed in the last 12 months, and not before: agents can finally *touch* hardware (MCP / Skill); agents can finally *do research* (workshop-grade output); a differentiable GPU physics base went open ([NVIDIA Newton](https://developer.nvidia.com/newton-physics), 2025); and base models got strong enough for multi-step autonomous loops. A year earlier, none of this works. This is the early window.

## 🤝 Get involved

This is a big puzzle, and we want sharp people on it.

- ⭐ **Star** if you think physical AI's missing piece is *grounding*, not scale.
- 💬 **[Discussions](https://github.com/DataFlux-Robot/FLUXLOOP/discussions)** — debate the sim2real-as-model-discovery thesis, or tell us what black-box hardware wrecked your last month.
- 🛠️ **Contribute** — real-time kernels, multiphysics, robot control, agent systems. The component repos have open issues.
- 🎁 **Crowdfunding (coming soon)** — `mini` & `pro` (see [Product Lineup](#-product-lineup)) go to an early-access campaign first. *(Reward tiers, price and shipping land at launch — watch this repo to be notified.)*

---

<p align="center">
  <sub><b>FLUXLOOP</b> · built by <b>DataFLUX Dynamics</b> · early & open<br/>
  <i>From auto-researching one piece of hardware, toward machines that research and improve themselves.</i></sub>
</p>
