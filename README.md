<p align="center">
  <img src="./assets/logo.png" alt="FLUXLOOP" width="420"/>
</p>

<p align="center">
  <i>An AI agent that brings up unknown hardware, learns its real physics, and writes the driver — on its own.</i>
</p>

<p align="center">
  <b>Opening the era of the physical one- / few- / zero-person company —<br/>when AI does the physical R&D, a tiny team can build real hardware.</b>
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

And along the way it changes **who** can build hardware at all. When the agent does the physical R&D, a one-person — or even zero-person — company can ship real, physical products. That is the era we are opening: the **physical one- / few- / zero-person company**.

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

## 📣 What developers are telling us

We didn't guess this problem — we went and listened (to high-signal hardware/embedded communities). A developer, arguing about whether AI is overhyped for embedded work, wrote (verbatim, translated):

> *"It's not that the model is dumb — it's that it never actually **sees** your hardware. The datasheet is read by OCR that can't even get the register bits right; the schematic is invisible to it; it just greps your whole codebase into context and the one register config that matters gets squeezed out. So you get: compiles clean, zero warnings — then a HardFault on the bench. For bare-metal, where one wrong bit loses everything, a generic agent simply can't do it yet."*

**That is FLUXLOOP's entire thesis — stated by someone who isn't us.** Across the threads we read, the signal was consistent: the pain is real, today's workarounds are manual (people hand-feed datasheets and libraries to the model), and there is real demand for a *hardware-grounded* agent.

→ Full market signal, quotes & methodology: **[MARKET_VALIDATION.md](./MARKET_VALIDATION.md)**

## 🧩 Built & validated

This is not slideware. Each component is a working repo, validated against gold standards:

| Layer | Component | What it is | Proof |
|---|---|---|---|
| 🧠 Mind | **[Flux-Insight](https://github.com/ExuberantWitness/Flux-Insight)** | Autonomous research engine — Claim-Chain knowledge graph + 21 composable skills | v0.3.0, active |
| 🌐 World | **[FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex)** | First-principles **aerodynamics** solver (GPU vortex method) | Goland flutter **2.4% err**, 97% Theodorsen |
| 🌐 World | **[FluxPhased](https://github.com/ExuberantWitness/FluxPhased-)** | **EM / phased-array** multiphysics sim (IQ-level) | MATLAB-validated **83/83**, ~985 sweeps |
| 🦾 Body | **[FluxTendril](https://github.com/DataFlux-Robot/FluxTendril)** | Real-time nervous system: protocol-unifying Actuator/Sensor Bridge + hardware root-of-trust | architecting |
| 🦾 Body | **[FluxTide](https://github.com/DataFlux-Robot/FluxTide)** | Universal robot controller — sample-based MPC + parallel envs | usable |
| 🦾 Body | **[FluxAxon](https://github.com/DataFlux-Robot/FluxAxon)** | Deterministic TSN-over-USB bridge — connects a host to the DataFlux nervous system | 🌱 early |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** · **[FluxPulse](https://github.com/DataFlux-Robot/FluxPulse)** | Power & bus backbone (GaN; interleaved / bidirectional) | v0 hardware |

> **Validated MVP:** an agent autonomously read the docs, drove an oscilloscope + relay, and wrote the driver itself.

## 🎁 Product Lineup

*Our roadmap, made tangible — every tier is both a product you can hold and a step toward the 2040 vision.*

Each tier runs the same **FLUXLOOP brain** (auto-research agent + physics simulator). What changes is **how much the agent can perceive and act** — the ladder climbs from *reading* a sensor → *seeing* the hardware → *moving to see it* → *acting on it* → *designing it*. The box handles real-time control and sensing; heavy reasoning and multiphysics simulation run in the cloud by default (or fully on-device with the Local AI Module).

| Tier | What's added | Best for | From |
|---|---|---|---|
| 🎟️ **Software / Early Access** | Agent + cloud, no hardware | Trying it, joining the community, giving feedback | ¥199 / $28 |
| ⚡ **MICRO** | Entry-tier on-board compute + cloud API | Makers, students, price-sensitive builders (reasoning runs in cloud) | ¥1,999 / $280 |
| 📦 **mini** | Mid-tier on-board edge compute | Hardware that already exposes its state via readable sensors | ¥5,999 / $845 |
| 📷 **pro** | + fixed camera · multimodal | Hardware with **no readable state sensor** — the camera becomes a virtual sensor | ¥6,999 / $985 |
| 🦾 **max** | + posable camera arm + base (à la [Kynooe](https://www.kynooe.com/)) | **Active perception** — the agent repositions to see occluded states | ¥15,999 / $2,250 |
| 🔧 **Local AI Module** *(add-on)* | High-performance on-board compute — runs the LLM **and** multiphysics sim locally | **Secure, data-never-leaves** deployments | +¥5,999 / +$845 |
| 🔮 **ultra / Ulti** | Modular humanoid → self-designing modules | The 2040 vision — **not for sale**, notify-me only | — |

> *Indicative early-bird pricing — final tiers, funding target, shipping and demos land with the crowdfunding campaign. `ultra` & `Ulti` are the vision we build toward, clearly marked and never sold ahead of what's real.*

### ☁️ Cloud & pricing — fair by design

By default the box handles control and sensing, while the **heavy LLM reasoning and GPU multiphysics simulation run in the cloud**. Our pricing philosophy is simple: **you pay for usage at near-cost, and we earn from the value we add — not by marking up your tokens.**

- **LLM** — usage-based, **3% above the official API price**
- **GPU compute (multiphysics simulation)** — **at market rate**

Want to self-host? Go ahead, it's open. Need everything on-prem for security? The **Local AI Module** runs the full loop with **zero data leaving your hardware**.

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
- 🎁 **Crowdfunding (coming soon)** — `Software`, `MICRO`, `mini` & `pro` (see [Product Lineup](#-product-lineup)) go to an early-access campaign first. *(Reward tiers, price and shipping land at launch — watch this repo to be notified.)*

## 📬 Contact

**Want to build this together, talk through the ideas, or invest?** Reach out.

<p align="center">
  <img src="./assets/wechat-qr.png" alt="WeChat" width="240"/><br/>
  <sub>Scan to add on WeChat — note "FLUXLOOP invest / dev / discuss"</sub>
</p>

Prefer GitHub? Open an [issue](https://github.com/DataFlux-Robot/FLUXLOOP/issues) or a [discussion](https://github.com/DataFlux-Robot/FLUXLOOP/discussions).

---

<p align="center">
  <sub><b>FLUXLOOP</b> · built by <b>DataFLUX Dynamics</b> · early & open<br/>
  <i>From auto-researching one piece of hardware, toward machines that research and improve themselves.</i></sub>
</p>
