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
  <img alt="status" src="https://img.shields.io/badge/status-early-orange">
  <img alt="license" src="https://img.shields.io/badge/license-open--core%20%28components%20Apache--2.0%29-blue">
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

**FLUXLOOP** closes it. It is an agent-led hardware-R&D system (open-core: components open, integrated product commercial): connect any actuator, sensor, or device — even one with no documentation, an undocumented protocol, and performance specs its own maker can't give you — and FLUXLOOP autonomously figures out how to talk to it, characterizes its true physical behavior, and produces a working driver. What costs a specialist weeks — protocol bring-up, sim-to-real calibration, driver development — it compresses into hours.

The system is organized around three layers. A **research brain** ([Flux-Insight / EvoScientist](https://github.com/ExuberantWitness/Flux-Insight)) proposes hypotheses, designs experiments, and — when parameter-tuning isn't enough — *discovers* new correction models via symbolic regression. A **precise multiphysics world** ([FLUXVortex](https://github.com/ExuberantWitness/FLUXVortex) for aerodynamics, [FluxPhased](https://github.com/ExuberantWitness/FluxPhased-) for electromagnetics) predicts behavior from first principles rather than from data-driven approximation. And a **real-time, secure body** ([FluxTendril](https://github.com/DataFlux-Robot/FluxTendril) + [FluxAxon](https://github.com/DataFlux-Robot/FluxAxon) + [FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)) lets the agent actually probe and drive physical hardware — the one place a cloud model can never reach.

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

## 🎬 Demo — real hardware test

A real test run on physical hardware (not a concept clip):

<video src="https://github.com/DataFlux-Robot/FLUXLOOP/raw/main/assets/demo-hardware-test.mp4" controls width="640"></video>

▶️ **[Watch the hardware test video](https://github.com/DataFlux-Robot/FLUXLOOP/raw/main/assets/demo-hardware-test.mp4)** (if the player doesn't load inline)

## 🧠 The thesis worth debating

> **We believe sim2real is a model-*discovery* problem, not a domain-randomization problem.**
>
> The mainstream approach learns approximate physics from massive data — and inherits its "physics slop." We do the opposite: solve precise physics from first principles, then let an agent *discover* the correction terms that close the gap to reality. For anything where physical precision actually matters, first-principles + a learned residual beats a data-driven world model.
>
> Think we're wrong? **[Open an issue and argue with us.](https://github.com/DataFlux-Robot/FLUXLOOP/issues)**

## 📣 What developers are telling us

We didn't guess this problem — we went and listened across hardware, embedded, and robotics communities. A developer, arguing about whether AI is overhyped for embedded work, wrote (verbatim, translated):

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
| 🦾 Body | **[FluxAxon](https://github.com/DataFlux-Robot/FluxAxon)** | Deterministic TSN-over-USB bridge — connects a host to the DataFlux nervous system | 🌱 early |
| 🔌 Body | **[FluxCurrent](https://github.com/DataFlux-Robot/FluxCurrent)** · **[FluxPulse](https://github.com/DataFlux-Robot/FluxPulse)** | Power & bus backbone (GaN; interleaved / bidirectional) | v0 hardware |

> **Validated MVP:** an agent autonomously read the docs, drove an oscilloscope + relay, and wrote the driver itself.

## 🎁 Product Lineup

*Our roadmap, made tangible — every tier is both a product you can hold and a step toward the 2040 vision.*

Each tier runs the same **FLUXLOOP brain** (auto-research agent + physics simulator). What changes is **how much the agent can perceive and act** — the ladder climbs from *using* a research library → *reading* a sensor → *seeing* the hardware → *moving to see it* → *acting on it* → *designing it*. The box handles real-time control and sensing; heavy reasoning and multiphysics simulation run in the cloud by default (or fully on-device with the Local AI Module).

| Tier | What's added | Best for | From |
|---|---|---|---|
| 🧠 **Node Base** | **DevelopReady asset library access** + Agent + cloud, no hardware | Directly use pre-researched device models | ¥49 / $9 one-time |
| ⚡ **Node Bridge** | Entry-tier on-board compute + cloud API | Makers, students, price-sensitive builders (reasoning runs in cloud) | ¥1,999 / $289 |
| 📦 **Node Aware** | Mid-tier on-board edge compute | Hardware with readable sensors | ¥5,999 / $849 |
| 📷 **Node Vision** | + fixed camera · multimodal | Hardware with **no readable state sensor** — the camera becomes a virtual sensor | ¥6,999 / $989 |
| 🦾 **Node Explore** | + posable camera arm + base (à la [Kynooe](https://www.kynooe.com/)) | **Active perception** — the agent repositions to see occluded states | ¥15,999 / $2,499 |
| 🔮 **Node Meta** | Modular humanoid → self-designing modules | The 2040 vision — **not for sale**, notify-me only | — |
| 🔧 **Local AI Module** *(add-on)* | High-performance on-board compute — runs the LLM **and** multiphysics sim locally | **Secure, data-never-leaves** deployments | +¥5,999 / +$849 |

> *Indicative early-bird pricing — final tiers, funding target, shipping and demos land with the crowdfunding campaign. `Node Meta` is the vision we build toward, clearly marked and never sold ahead of what's real.*

**Naming philosophy:** Base → Bridge → Aware → Vision → Explore → Meta. Base (basic thinking) → Bridge (bridge to the physical world) → Aware (sense state) → Vision (see the hardware) → Explore (active perception) → Meta (self-design).

### 🧠 DevelopReady

NVIDIA defined *SimReady* — assets that can be simulated. We go further: assets that can be **directly driven, calibrated, and deployed**. Every device FLUXLOOP researches produces a DevelopReady model — not just a simulation twin, but a working driver, a calibrated performance model, and the proprietary correction terms discovered along the way.

### 🌐 Shared Cognitive Pool

Every device FLUXLOOP researches produces a DevelopReady model that flows back into a shared cognitive pool. User A's research on a motor becomes User B's starting point — not from zero, but with prior accumulated knowledge.

**Access model:**
- **One-time purchase** → access to a few fixed/preinstalled models
- **Membership (¥49-199/mo)** → full read access to the entire pool; contributing to the public pool is included
- **Private models** → additional fee (for enterprise / confidentiality needs)

This is the data flywheel: more users → more device models → faster onboarding for the next user → more valuable product → more users.

### 🔄 The loop that feeds itself

> **We use FLUXLOOP to build FLUXLOOP.** Every device we research sharpens the system for everyone. By launch: **200+ device models already in the pool.**

We are our own harshest first user — the node autonomously researches every device it touches (joint modules, sensors, actuators), pushing electronic assets from SimReady to DevelopReady. Each model goes straight back into the shared cognitive pool. The product our first backer receives isn't a blank system — it's one that has already "read" hundreds of devices.

### ☁️ Cloud & pricing — fair by design

The box handles control and sensing, while the **heavy LLM reasoning and GPU multiphysics simulation run in the cloud** by default. Our pricing philosophy: **three tiers, transparent usage, no token markup.**

- **One-time purchase (tier price)** → basic features + access to a few fixed cognitive pool models
- **Membership ¥49-199/mo** → full solver access + full cognitive pool read + advanced agent orchestration + public pool contribution included. **Crowdfunding tiers include 1 year of membership.**
- **Usage-based (transparent):**
  - **Token (LLM)** — **3% above official API price** (near-cost)
  - **GPU compute (multiphysics simulation)** — **at low market rate**
- **Private model storage** → additional fee (enterprise / confidentiality)

Need everything on-prem for security? The **Local AI Module** runs the full loop with **zero data leaving your hardware**.

## ✅ Status — honest

Phase 0 is shipped. Phase 1 is live: the **electrical loop is closed** (agent → probe → driver), and our multiphysics today covers **aerodynamics + electromagnetics** (thermal is next). End-to-end integration and the unknown-protocol auto-discovery product are in active development. Phases 2–4 are the north star.

**We don't claim we're there. We claim every step has real code under it — and we show it.** That's the whole point.

## ⏱️ Why now

Six thresholds were crossed in the last 12 months, and not before:

1. **Software multiplied by AI, physics didn't keep up.** Internal data shows engineer output has grown several-fold with AI — but that acceleration is entirely on the software side. Physical verification is still a traditional engineering team's job.
2. **Agents can finally touch hardware.** MCP / Skill protocols + purpose-built hardware bridges — the agent can finally take real data from the physical world. 2024 H2 was the crossover.
3. **Physics simulation ecosystem just settled.** Isaac Lab / USD / [NVIDIA Newton](https://developer.nvidia.com/newton-physics) established mainstream positions in 2025 — a standardized physics base now exists.
4. **Agents can finally do research.** Automated research has progressed to produce workshop-grade papers — proof that agents can handle mid-level engineering R&D.
5. **Software-side recursive self-improvement is racing ahead; physics-side is a blank.** Agent-training-agent loops already produce real results, but "agent autonomously doing physical research" remains untouched.
6. **Base models are just strong enough.** They can now sustain multi-step autonomous loops (hypothesis → experiment → analysis → correction).

A year earlier, none of this works. This is the early window.

## 🤝 Get involved

This is a big puzzle, and we want sharp people on it.

- ⭐ **Star** if you think physical AI's missing piece is *grounding*, not scale.
- 💬 **[Discussions](https://github.com/DataFlux-Robot/FLUXLOOP/discussions)** — debate the sim2real-as-model-discovery thesis, or tell us what black-box hardware wrecked your last month.
- 🛠️ **Contribute** — real-time kernels, multiphysics, robot control, agent systems. The component repos have open issues.
- 🎁 **Crowdfunding (coming soon)** — `Node Base`, `Node Bridge`, `Node Aware` & `Node Vision` (see [Product Lineup](#-product-lineup)) go to an early-access campaign first. *(Reward tiers, price and shipping land at launch — watch this repo to be notified.)*

## 🙏 Acknowledgements

- Thanks to the **MiMo Orbit 100T Token Creator Incentive Program** for providing compute resources for the development of our key components.
- Thanks to **Xiaomi** for **MiMo-V2.5-Pro-UltraSpeed** beta access. Its 1000+ tps inference lets the agent explore dozens of hypotheses in parallel with self-verification (e.g. Best-of-N protocol guessing on a black-box device), which materially helped us validate the system's usability.

## 📬 Contact

**Want to build this together, talk through the ideas, or invest?** Reach out.

<p align="center">
  <img src="./assets/wechat-qr.png" alt="WeChat" width="240"/><br/>
  <sub>Scan to add on WeChat — note "FLUXLOOP invest / dev / discuss"</sub>
</p>

Prefer GitHub? Open an [issue](https://github.com/DataFlux-Robot/FLUXLOOP/issues) or a [discussion](https://github.com/DataFlux-Robot/FLUXLOOP/discussions).

---

<p align="center">
  <sub><b>FLUXLOOP</b> · built by <b>DataFLUX Dynamics</b> · early · open-core<br/>
  <i>From auto-researching one piece of hardware, toward machines that research and improve themselves.</i></sub>
</p>
