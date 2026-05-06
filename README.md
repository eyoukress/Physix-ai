# PhysiX AI

**AI-powered physics simulation debugging agent** — detects numerical instability, explains root causes, and suggests fixes automatically.

> Built by **eyoukress** · Aurora Stage 2 · SDG 9 — Industry, Innovation and Infrastructure

---

## What It Does

Physics simulations fail constantly in game engines, robotics, and scientific research — energy drifts, values explode, systems diverge. Debugging these failures manually is slow and requires deep expertise.

PhysiX AI analyzes simulation behavior automatically and gives developers:

- A **0–100 stability score** across energy, oscillation, acceleration, and stiffness
- **Plain-language root-cause explanations** ("Your timestep is too large for the Euler integrator")
- **Specific parameter fix suggestions** ("Reduce Δt from 0.05 to 0.01, switch to RK4")
- **Visual playback** of the simulation so you can see the failure in real time

---

## Features

| Feature | Description |
|---|---|
| 🔬 **Physics Engine** | Spring-mass chains, damped pendulum, double pendulum (chaotic), orbital mechanics, 3-body gravity |
| ⚙️ **Integrators** | Euler, Semi-Euler (Symplectic), Velocity Verlet, RK4 |
| 📊 **Stability Analyzer** | Energy drift, oscillation growth, acceleration spikes, stiffness index — scored 0–100 |
| 🤖 **AI Debugging Agent** | Root-cause analysis + fix suggestions via AI backend with local reasoning fallback |
| 🎬 **Live 2D Animation** | Real-time canvas playback of recorded simulation frames with speed control |
| 🗺️ **Stability Heatmap** | Scans 100 combinations of Δt vs damping — shows safe vs explosive parameter regions |
| 📋 **Session History** | Logs every run with score, cause, and sparkline chart showing improvement over time |
| 🧊 **3D Viewer** | Three.js 3D visualization of simulation data with orbit controls |
| ⚖️ **Run Comparison** | Save two runs as A/B and compare stability metrics side by side |
| 📂 **Log Upload** | Upload external CSV/JSON simulation logs for analysis |
| 🔧 **Auto-Tune** | AI tests 10 parameter combinations and picks the most stable one |
| 📈 **Integrator Benchmark** | Compares all integrators on your exact system |
| ⚡ **Quick Auto-Fix** | One-click parameter correction based on detected root cause |

---

## Quick Start

No install. No dependencies. No server.

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/physix-ai.git
cd physix-ai

# Open directly in any browser
open index.html
```

Or just open `index.html` directly in Chrome, Firefox, or Edge.

---

## File Structure

```
physix-ai/
├── index.html          # Entire application — single self-contained file
├── README.md           # This file
├── LICENSE             # MIT License
└── .gitignore
```

The entire app ships as a single HTML file with no external dependencies beyond CDN-loaded libraries (Chart.js, Three.js, Google Fonts) — all loaded at runtime.

---

## How to Demo (Best Flow for Judges)

1. Open `index.html` in browser
2. Select **Double Pendulum** system, load **Chaotic** preset → hit **Run & Analyze**
3. Watch the stability score drop — open **Events** and **Root Causes** tabs
4. Switch to **🎬 Live Sim** tab — watch the chaotic playback
5. Hit **⚡ Quick Auto-Fix** → run again → score improves
6. Open **🗺 Heatmap** → Generate Heatmap — see which parameter regions are safe
7. Open **📋 History** — see the improvement from run 1 to run 2
8. Switch to **🧊 3D View** for spatial visualization

---

## Technical Architecture

```
Input Parameters (dt, mass, spring constant, damping, system type)
        │
        ▼
┌─────────────────────────────┐
│     Simulation Engine        │  Euler / Verlet / RK4 integration
│  Spring-Mass · Pendulum      │  Records position, velocity,
│  Double Pendulum · Orbital   │  acceleration, energy per tick
│  3-Body Gravity              │
└──────────────┬──────────────┘
               │ time-series data
               ▼
┌─────────────────────────────┐
│     Stability Analyzer       │  Energy drift detector
│                              │  Oscillation analyzer
│  Score: 0 ──────────── 100  │  Spike detector
│         ↑               ↑   │  Stiffness index
│       Chaos           Stable │
└──────────────┬──────────────┘
               │ diagnostic signals
               ▼
┌─────────────────────────────┐
│     AI Debugging Agent       │  Interprets signals
│                              │  Generates root-cause text
│  "Euler + large dt =         │  Recommends parameter fixes
│   energy growth"             │  Optional cloud backend
└──────────────┬──────────────┘
               │ analysis output
               ▼
┌─────────────────────────────┐
│    Visualization Interface   │  Charts · Score Ring
│                              │  Live 2D Animation
│  Dashboard · Heatmap         │  3D Three.js Viewer
│  History · Compare           │  Heatmap · Session Log
└─────────────────────────────┘
```

---

## SDG Alignment

**SDG 9 — Industry, Innovation and Infrastructure**

PhysiX AI democratizes access to expert-level simulation diagnostics. By making physics debugging faster and more accessible, it enables developers, students, and researchers to build and maintain complex physical systems — accelerating innovation in game development, robotics, and scientific computing.

Target impact: **3× reduction in simulation debugging time**.

---

## Future Roadmap

- [ ] External simulation log upload from Unity / Unreal / ROS
- [ ] Reinforcement learning for automatic parameter tuning
- [ ] 3D visualization of failure zones and instability propagation
- [ ] Multi-user collaboration and shared debugging sessions
- [ ] REST API for integration into CI/CD pipelines

---

## License

MIT — see [LICENSE](LICENSE)
