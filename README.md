<div align="center">

<img src="./assets/echo-terminal.svg" width="900" alt="Echo terminal interface" />

# Jesus999l / Echo Lab

**Local-first AI • systems engineering • automation • perception • privacy**

Building **Echo** — a local-first AI companion and experimental personal-computing environment focused on memory, voice, perception, automation, research, and long-lived human-computer interaction.

</div>

<p align="center">
  <a href="https://github.com/jeantimex/neofetch-profile">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://neofetch-profile.vercel.app/api?username=jesus999l&theme=github-dark&config=https%3A%2F%2Fraw.githubusercontent.com%2Fjesus999l%2Fjesus999l%2Fmain%2Fneofetch.json">
      <img alt="Terminal-style GitHub profile with avatar and Echo system information" src="https://neofetch-profile.vercel.app/api?username=jesus999l&theme=github-light&config=https%3A%2F%2Fraw.githubusercontent.com%2Fjesus999l%2Fjesus999l%2Fmain%2Fneofetch.json">
    </picture>
  </a>
</p>

> The terminal-style panel above is intentional: it is the **profile presentation**, not a replacement for the README. The README remains documentation-first.

---

## `echo@local:~$ status`

```text
[ OK ] Echo research / orchestration
[ OK ] Desktop perception experiments
[ OK ] Wayland / DriftWM exploration
[ OK ] Offline voice stack experiments
[ OK ] Manhua research + preprocessing prototype
[ OK ] Research distillation / deduplication tooling
[ OK ] Cloud-connected storage research
[WIP ] Full perception → reasoning → automation loop
```

The goal is not another chatbot. The goal is a private computing system that can **observe, reason, remember, act, and verify** while keeping important pieces local and auditable.

## Quick Start

The profile repository is documentation and project navigation. It does **not** pretend that every Echo subsystem is production-ready.

```bash
git clone https://github.com/jesus999l/jesus999l.git
cd jesus999l
```

### Install / build guides

| Guide | Purpose |
|---|---|
| [Installation](./docs/guides/install.md) | Host setup, prerequisites, and component installation |
| [Run locally](./docs/guides/run-local.md) | Start and verify local Echo components |
| [Docker services](./docs/guides/docker-services.md) | Supporting services and container workflow |
| [Project map](./docs/projects.md) | What each subsystem is and how it fits together |
| [DriftWM](./docs/driftwm.md) | Wayland compositor work |
| [Security](./docs/security/) | Public/private boundaries and safety notes |

---

## Featured Work

| Project | What it is | Status |
|---|---|---|
| **[Echo Vision](https://github.com/jesus999l/echo-vision)** | Perception and computer-vision experiments for Echo | Active |
| **[LatentBox](https://github.com/jesus999l/latentbox)** | AI / creativity resource collection | Public |
| **Echo** | Local-first assistant architecture, memory, voice, automation | Active / WIP |
| **DriftWM** | Experimental Wayland compositor work | Experimental |
| **Echo Research Lab** | Research, distillation, deduplication, media and knowledge pipelines | Experimental |

## Echo Architecture

```text
                    ┌──────────────────────┐
                    │       Echo UI        │
                    │ desktop / web / phone│
                    └──────────┬───────────┘
                               │
                    ┌──────────▼───────────┐
                    │      Orchestrator    │
                    │ events / tools / flow│
                    └──────┬───────┬───────┘
                           │       │
              ┌────────────▼─┐   ┌─▼─────────────┐
              │   Perception │   │  Local Models │
              │ state / voice│   │ llama.cpp etc. │
              └──────┬───────┘   └──────┬─────────┘
                     │                  │
                     └────────┬─────────┘
                              ▼
                       ┌──────────────┐
                       │ Memory / RAG │
                       │ knowledge    │
                       └──────┬───────┘
                              ▼
                       ┌──────────────┐
                       │ Tools / Act  │
                       │ automation   │
                       └──────┬───────┘
                              ▼
                       ┌──────────────┐
                       │   Verify     │
                       │ observe again│
                       └──────────────┘
```

The architecture is intentionally incremental: **prove primitives first, then connect them**.

## Current Research Tracks

- **Perception** — structured desktop state, accessibility metadata, screenshots, and visual fallback paths.
- **Voice** — offline speech recognition and local text-to-speech experiments.
- **Automation** — controlled task execution with explicit safety boundaries.
- **Knowledge** — research pipelines, distillation, deduplication, evidence-oriented notes, and persistent context.
- **Media** — manga/manhwa acquisition research, OCR, panel processing, chapter assembly, and recap preprocessing.
- **Investing research** — public market concepts, portfolio research, trading-bot ecosystems, and evidence collection; research only, not financial advice.
- **Infrastructure** — Docker, local services, object storage, synchronization, and privacy-conscious cloud persistence.

## Components

### Echo Kernel
Orchestration and event flow between models, memory, tools, interfaces, and automation.

→ [System documentation](./docs/system/echo-kernel.md)

### Memory Vault
Persistent context, knowledge relationships, retrieval, and long-lived state.

→ [Memory documentation](./docs/system/memory-vault.md)

### Voice Pipeline
Wake-word, speech-recognition, and local TTS experiments using the offline-first stack.

→ [Voice documentation](./docs/system/voice-pipeline.md)

### DriftWM
Rust / Wayland / Smithay compositor experimentation for an AI-native desktop environment.

→ [DriftWM notes](./docs/driftwm.md)

### Research Laboratory
Automated collection, normalization, quality filtering, distillation, deduplication, and research-output generation.

→ [Project map](./docs/projects.md)

---

## `echo@local:~$ principles`

```text
local-first        → cloud is an extension, not the brain
privacy             → minimize secrets and unnecessary telemetry
auditable           → prefer inspectable pipelines over magic
incremental         → prove primitives before connecting subsystems
reversible          → back up before modifying working systems
useful              → build things that survive contact with reality
```

## Documentation Map

- [Project map](./docs/projects.md)
- [Installation](./docs/guides/install.md)
- [Run locally](./docs/guides/run-local.md)
- [Docker services](./docs/guides/docker-services.md)
- [DriftWM](./docs/driftwm.md)
- [Philosophy](./docs/philosophy.md)
- [Security](./docs/security/)
- [System documentation](./docs/system/)
- [Design notes](./docs/design/)
- [Agent / tool notes](./docs/agents/)
- [Demos](./demos/)

## Public Repositories

- [echo-vision](https://github.com/jesus999l/echo-vision)
- [latentbox](https://github.com/jesus999l/latentbox)
- [Profile / Echo Lab](https://github.com/jesus999l/jesus999l)

---

<div align="center">

```text
┌──────────────────────────────────────────────────────────────┐
│  echo@local                                                  │
│  ├── perceive                                                │
│  ├── remember                                                │
│  ├── reason                                                  │
│  ├── act                                                     │
│  └── verify                                                  │
│                                                              │
│  BUILDING A COMPUTER, NOT JUST A CONVERSATION.               │
└──────────────────────────────────────────────────────────────┘
```

</div>
