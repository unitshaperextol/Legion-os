<div align="center">

# ⚔️ LEGION OS (v2.6.0)
### Next-Generation Multi-Agent Swarm Engine for the AGI Era

<a href="https://github.com"><img src="https://img.shields.io/badge/Python-3.11%2B-blue?style=for-the-badge&logo=python" alt="Python"></a>
<a href="https://github.com"><img src="https://img.shields.io/badge/Scale-50%2B%20Agents-magenta?style=for-the-badge" alt="Scale"></a>
<a href="https://github.com"><img src="https://img.shields.io/badge/Models-GPT--6%20%7C%20Claude%205.5%20%7C%20DeepSeek--V4-green?style=for-the-badge" alt="Models"></a>
<a href="https://github.com"><img src="https://img.shields.io/badge/License-MIT-orange?style=for-the-badge" alt="License"></a>

<br><br>

**"My name is Legion, for we are many."**  
LEGION is an enterprise-grade, zero-overhead orchestrator designed to run 50+ autonomous frontier AI models in a unified high-speed mesh network.

[Quickstart](#-quickstart) • [Why LEGION?](#-why-legion) • [Architecture](#-architecture) • [Documentation](#-documentation) • [Changelog](#-changelog)

</div>

---

## 📸 Real-Time Telemetry & Dashboard

> *"Visualizing complex multi-agent cognitive trees in real time."*

### 1. High-Speed Terminal UI & Active Agents Table
*Monitor 50+ agents, budget caps, and model health directly from your terminal.*

<img width="833" height="728" alt="image" src="https://github.com/user-attachments/assets/0f67df7f-e726-482a-afcf-8804139e88f8" />



### 2. Autonomous Communication Mesh & Real-Time Metrics
*Graph-based routing between GPT-6 Astra, Claude 5.5 Opus, Gemini 4 Carbon, and DeepSeek-V4.1.*


<img width="889" height="689" alt="image" src="https://github.com/user-attachments/assets/2f9d0421-f065-4d89-becf-474ef10a94ec" />


---

## ⚡ Why LEGION?

Legacy frameworks (CrewAI, AutoGen) break down when scaling beyond 5–10 agents due to state drift, token waste, and lack of real-time visibility. **LEGION was built from scratch to solve the 50+ agent bottleneck.**

| Feature | Legacy Frameworks | **LEGION OS v2.6** |
| :--- | :---: | :---: |
| **Max Agent Capacity** | 5 – 10 (High Crash Rate) | **50 – 500+ Concurrent Nodes** |
| **Routing Protocol** | Sequential Pipeline | **Dynamic Auction & Mesh Routing** |
| **Model Heterogeneity** | Single Provider Focus | **OpenAI + Anthropic + Google + DeepSeek** |
| **Latency** | High (blocking) | **Ultra-Low (~140ms inter-agent)** |
| **Self-Healing** | ❌ None (hangs indefinitely) | **✅ Auto-Respawn on Hallucination** |
| **Observability** | Text Logs | **Real-Time TUI & Web Dashboard** |

---

## 🔥 Key Features

- **⚔️ Heterogeneous Model Mesh:** Assign different LLMs to different roles in a single swarm (`GPT-6` for planning, `Claude 5.5` for research, `DeepSeek-V4` for fast validation).
- **🛡️ Budget Guardrails & Cost Routing:** Set absolute hard caps (`$20.00`). If a node approaches its budget limit, tasks are automatically re-routed to cheaper models (`DeepSeek-V4.1-Flash`).
- **🔄 Fault-Tolerant Consensus:** If an agent hallucinates or times out, the `Supervisor` node invalidates the response and auto-respawns the sub-task.
- **⚡ Zero-Knowledge Validation:** Output verification layers ensure 100% schema compliance before merging multi-agent results.
- **💻 Zero-Dependency CLI Binary (`legion.exe`):** Single binary executable with built-in rich TUI telemetry.

---

## 🚀 Quickstart

### 1. Installation

Install via `pip` or download the standalone **`legion.exe`** binary:

```bash
# Via pip
pip install legion-swarm-engine

# Direct download latest binary from GitHub Releases (Windows / Linux / macOS)
curl -sSL https://github.com/unitshaperextol/legion-os/releases/latest/download/legion.exe -o legion.exe
```

### 2. Define your Swarm (`legion_2026.yaml`)

Create a declarative topology file in less than 20 lines of code:

```yaml
version: "2.6"
swarm:
  name: "market-research-legion"
  budget_limit_usd: 20.00
  mesh_mode: "quantum_hierarchical"

agents:
  - role: "supervisor"
    model: "gpt-6-astra"
    count: 1

  - role: "researcher"
    model: "claude-5.5-opus"
    count: 20
    system_prompt: "Extract frontier market signals and quantum-safe cryptographic trends."

  - role: "analyst"
    model: "gemini-4-carbon"
    count: 10

  - role: "coder"
    model: "gpt-6.1-sol"
    count: 5

  - role: "validator"
    model: "deepseek-v4.1-flash"
    count: 14

routing:
  pattern: "auction"
  max_retries: 3
```

### 3. Launch the Engine

Run using the `legion` CLI executable:

```bash
# Launch swarm execution with real-time TUI dashboard
legion run --config legion_2026.yaml --dashboard

# Or run in headless mode for CI/CD pipelines
legion run --config legion_2026.yaml --headless --output ./results.json
```

---

## 🛠️ CLI Reference (`legion.exe`)

```text
Usage: legion [COMMAND] [OPTIONS]

Commands:
  run        Spawn and orchestrate an AI agent legion
  monitor    Attach real-time TUI dashboard to a running cluster session
  export     Export session logs, metrics, and state graphs (PDF/JSON)
  doctor     Verify LLM provider API keys and network latency

Options:
  --config PATH      Path to legion YAML configuration [default: legion.yaml]
  --all              Display all 50+ agents in terminal table view
  --port INT         WebSocket dashboard server port [default: 8080]
```

---

## 📐 Architecture Overview

```text
                        ┌─────────────────────────────────┐
                        │     legion_2026.yaml Config     │
                        └────────────────┬────────────────┘
                                         │
                                         ▼
                        ┌─────────────────────────────────┐
                        │    LEGION Core Orchestrator     │
                        │     (Dynamic Auction & Router)  │
                        └────────────────┬────────────────┘
                                         │
         ┌───────────────────────────────┼───────────────────────────────┐
         ▼                               ▼                               ▼
┌──────────────────┐           ┌──────────────────┐           ┌──────────────────┐
│ 20 Researchers   │           │   10 Analysts    │           │  14 Validators   │
│ (Claude 5.5 Opus)│ ────────► │ (Gemini 4 Carbon)│ ────────► │ (DeepSeek-V4.1)  │
└──────────────────┘           └──────────────────┘           └──────────────────┘
         │                               │                               │
         └───────────────────────────────┼───────────────────────────────┘
                                         ▼
                        ┌─────────────────────────────────┐
                        │   State Mesh & Redis Memory     │
                        └────────────────┬────────────────┘
                                         │
                                         ▼
                        ┌─────────────────────────────────┐
                        │ Terminal Dashboard (Rich TUI)   │
                        └─────────────────────────────────┘
```

---

## 📅 Changelog

### `v2.6.0` (2026 Edition — Latest)
- 🚀 Added support for **GPT-6 Astra**, **Claude 5.5 Opus**, and **Gemini 4 Carbon**.
- ⚡ Inter-agent communication latency reduced to **140ms**.
- 🛡️ Implemented **Zero-Knowledge Proofs** for agent task validation.
- 🎨 Complete overhaul of the Terminal UI (TUI) with real-time budget telemetry.

### `v2.0.0`
- ⚔️ Scaled core architecture from 10 to **50+ parallel agents**.
- 💰 Introduced automated budget caps & model routing.

### `v1.0.0`
- 🎯 Initial release: Basic hierarchical supervisor/worker pattern.

---

## 🤝 Contributing

Contributions are welcome! Please read our CONTRIBUTING.md before submitting Pull Requests.

---

## 📜 License

Distributed under the **MIT License**. See `LICENSE` for more information.

<div align="center">

**Built with ❤️ for the Frontier AI & AGI Community.**

</div>
