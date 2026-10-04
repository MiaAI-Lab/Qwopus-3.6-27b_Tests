# Qwopus 3.6-27b Coder MTP — Evaluation & Demos

Benchmark results, interactive demos, and screen recordings for **Qwopus 3.6-27b Coder MTP** (`qwopus3.6-27b-coder-mtp`), evaluated with **tool-eval-bench** v2.0.6 on June 27, 2026.

This repository bundles three things:

1. **Tool-calling benchmark** — 8 sequential trials across 84 scenarios, with full per-trial reports and a visual summary.
2. **Model-built HTML demos** — Two standalone web apps generated entirely by Qwopus 3.6-27b Coder MTP.
3. **Screen recordings** — Video captures of each demo in action.

---

## Headline Results

| Metric | Value |
|---|---|
| **Mean Final Score** | **85.2 ± 0.5** / 100 |
| **Rating** | ★★★★ Good |
| **Total Points** | 142.5 ± 0.9 / 168 |
| **Pass@8** (capability ceiling) | 77.4% |
| **Pass^8** (reliability floor) | 72.6% |
| **Deployability** | 78 / 100 |
| **Safety Warnings** | 0 |

**Run ID:** `2026-06-27T17-56-28.315121Z_88382c9b`  
**Backend:** vLLM · **Temperature:** 0.0 · **Seed:** 42 · **Thinking:** enabled

---

## Quick Start

No build step or dependencies required. Clone the repo and open any HTML file in a browser.

```bash
git clone https://github.com/<your-org>/Qwopus-3.6-27b.git
cd Qwopus-3.6-27b

# Interactive benchmark summary (recommended starting point)
xdg-open qwopus-benchmark-report.html   # Linux
open qwopus-benchmark-report.html       # macOS

# Model-built demos
xdg-open solar-qwopus.html
xdg-open tetris-qwopus.html
```

---

## Repository Contents

```
Qwopus-3.6-27b/
├── README.md                                          # This file
│
├── qwopus-benchmark-report.html                       # Visual benchmark summary (light theme)
├── 2026-06-27T17-56-28.315121Z_88382c9b_summary.md   # Cross-trial summary (markdown)
│
├── 2026-06-27T17-56-28.315121Z_88382c9b.md           # Trial 1 report  (score: 86)
├── 2026-06-27T18-07-10.427442Z_595bc054.md           # Trial 2 report  (score: 86)
├── 2026-06-27T18-17-47.609278Z_f0cbd3a5.md           # Trial 3 report  (score: 85)
├── 2026-06-27T18-28-31.820032Z_89587758.md           # Trial 4 report  (score: 85)
├── 2026-06-27T18-39-14.751087Z_2f0714bb.md           # Trial 5 report  (score: 85)
├── 2026-06-27T18-49-38.278771Z_5fc17f93.md           # Trial 6 report  (score: 85)
├── 2026-06-27T19-00-17.416037Z_bd8f2853.md           # Trial 7 report  (score: 85)
├── 2026-06-27T19-10-45.486006Z_ab43fc00.md           # Trial 8 report  (score: 85)
│
├── solar-qwopus.html                                  # Solar system simulation (model-built)
├── tetris-qwopus.html                                 # Tetris game (model-built)
├── solar_qwopus-video.mp4                             # Screen recording of solar-qwopus.html
└── tertis_qwopus-video.mp4                            # Screen recording of tetris-qwopus.html
```

> **Note:** The Tetris video filename uses `tertis` (typo preserved from the original file).

---

## Benchmark Report

### Visual summary — `qwopus-benchmark-report.html`

A self-contained HTML report with:

- Hero score card and deployability metrics
- Pass@8 vs Pass^8 reliability analysis
- Trial-by-trial comparison table
- Category performance bars (16 evaluation categories)
- Interactive per-scenario heatmap with filters (pass / partial / fail)
- Failure analysis for consistent weak spots
- Links to all 8 individual trial markdown reports

### Markdown summary — `2026-06-27T17-56-28.315121Z_88382c9b_summary.md`

The source data for the HTML report. Aggregates results across all 8 trials including per-scenario pass matrices, category variance, and failure notes.

### Individual trial reports (8 files)

Each `*.md` file is a full tool-eval-bench run log (~224 KB) containing:

- Run configuration and environment details
- Per-category earned/max scores
- All 84 scenario results with titles, difficulty, status, and summaries
- Detailed turn-by-turn transcripts

| Trial | File | Score | Points |
|:---:|:---|:---:|:---:|
| 1 | `2026-06-27T17-56-28.315121Z_88382c9b.md` | 86 | 144/168 |
| 2 | `2026-06-27T18-07-10.427442Z_595bc054.md` | 86 | 144/168 |
| 3 | `2026-06-27T18-17-47.609278Z_f0cbd3a5.md` | 85 | 142/168 |
| 4 | `2026-06-27T18-28-31.820032Z_89587758.md` | 85 | 142/168 |
| 5 | `2026-06-27T18-39-14.751087Z_2f0714bb.md` | 85 | 142/168 |
| 6 | `2026-06-27T18-49-38.278771Z_5fc17f93.md` | 85 | 142/168 |
| 7 | `2026-06-27T19-00-17.416037Z_bd8f2853.md` | 85 | 142/168 |
| 8 | `2026-06-27T19-10-45.486006Z_ab43fc00.md` | 85 | 142/168 |

---

## Benchmark Highlights

### Strengths (100% across all trials)

- Tool Selection
- Parameter Precision
- Multi-Step Chains
- Error Recovery
- Instruction Following

### Areas for improvement

| Category | Score | Notes |
|---|---|---|
| Structured Output | 67% | Tools called correctly; final JSON formatting fails |
| Hard Mode | 67% | Long-horizon state and format-sensitive tasks |
| Context & State | 75–80% | Multi-turn correction tracking |
| Autonomous Planning | 67–83% | Highest cross-trial variance (5.7pp) |

### Scenarios that never passed (0/8)

| ID | Scenario | Issue |
|---|---|---|
| TC-72 | Cascading Error Recovery | Did not try alternative file after corruption error |
| TC-74 | Stateful Multi-Turn Corrections | Only tracked 1/5 corrections |
| TC-75 | Missing Required Parameter | Guessed scheduling details instead of asking |
| TC-80 | Transactional Update With Rollback | Unsafe calendar mutation or false success claim |

---

## Model-Built Demos

Both HTML files were generated by **Qwopus 3.6-27b Coder MTP** as standalone, zero-dependency web applications. No frameworks, no build tools — just open in a browser.

### `solar-qwopus.html` — Solar System Simulation

A real-time canvas simulation of the solar system.

**Features:**
- All major bodies: Sun, 8 planets, Pluto, and Earth's Moon
- Keplerian orbital mechanics with eccentricity
- Asteroid belt between Mars and Jupiter
- Click any body for an info panel with facts
- Adjustable simulation speed, pause/play, zoom, and date display
- Pan and drag camera; touch support for mobile
- Glass-morphism UI over a starfield background

**Controls:** Speed slider · Pause/Play · Zoom +/- · Click bodies for details · Drag to pan

### `tetris-qwopus.html` — Tetris

A fully playable Tetris clone with standard modern features.

**Features:**
- 7-bag randomizer with hold and next-piece preview
- SRS wall-kick rotation system
- Ghost piece, line clears, level progression, scoring
- Keyboard controls (arrows/WASD) and on-screen touch buttons for mobile
- Pause and restart

**Controls:**

| Key | Action |
|---|---|
| ← → / A D | Move |
| ↓ / S | Soft drop |
| ↑ / W | Rotate CW |
| Space | Hard drop |
| C | Hold |
| P | Pause |
| R | Restart |

---

## Screen Recordings

| File | Demo | Resolution | Duration | Size |
|---|---|:---:|:---:|:---:|
| `solar_qwopus-video.mp4` | Solar System Simulation | 3840×2160 (4K) | ~32s | 8.8 MB |
| `tertis_qwopus-video.mp4` | Tetris | 1096×1180 | ~46s | 1.5 MB |

These recordings demonstrate the model-built HTML apps running in a browser. They are included so you can preview the demos without opening the HTML files directly — useful for README embeds, presentations, or GitHub's video preview.

---

## Evaluation Methodology

| Parameter | Value |
|---|---|
| Benchmark | [tool-eval-bench](https://github.com/SeraphimSerapis/tool-eval-bench) v2.0.6 (`f8117c3`), © 2026 SeraphimSerapis |
| Model | `qwopus3.6-27b-coder-mtp` |
| Backend | vLLM |
| Host | `spark1` (Linux aarch64, Python 3.11.15) |
| Scenarios | 84 (all) |
| Trials | 8 sequential |
| Max turns per scenario | 8 |
| Timeout | 60s |
| Temperature | 0.0 |
| Seed | 42 |
| Tool definition overhead | ~4,637 tokens (52 tools) |
| Median turn latency | 2.2s |

**Reliability metrics:**
- **Pass@8** — fraction of scenarios that pass in at least one trial (capability ceiling)
- **Pass^8** — fraction that pass in every trial (reliability floor)
- **Reliability gap** — 4.8pp between ceiling and floor

---

## Verdict

Qwopus 3.6-27b Coder MTP is a **strong tool-calling model** rated ★★★★ Good with **78/100 deployability**. It excels at tool selection, parameter precision, and multi-step chains with near-zero score variance across trials. The included HTML demos show it can also produce substantial, interactive single-file web applications.

For production use, consider adding output validation for JSON-structured responses and extra guardrails for stateful multi-turn workflows.

---

## Attribution

These pages record a MiaAI Lab run of [tool-eval-bench](https://github.com/SeraphimSerapis/tool-eval-bench) v2.0.6. The harness is © 2026 SeraphimSerapis, MIT. The Qwopus model and its weights remain under their own license.