## Ansh Jerath

Final-year CS student at VIT Vellore. I build systems where AI does the decision-support work but arithmetic and physics do the actual deciding.

---

### What I'm working on

Finishing **Samsung PRISM Worklet** — a cost-aware framework for detecting synthetic data (AI-generated text, images, audio, video) in data acquisition pipelines. The text detector is complete (95.3% accuracy / 92.84% F1 on HC3). The four-modality fusion engine is running; the accuracy KPI is currently gated on acquiring a labeled validation dataset. The project status doc is updated as things change and doesn't claim more than what's been measured.

Also in the research phase for **CAPS-FCL**, a contamination-aware waste segregation system combining computer vision, IoT sensor fusion, and federated learning. I'm currently in the literature phase — having systematically reviewed 30 papers (DOIs cross-referenced and verified) and searched 22 prior-art patents — establishing the theoretical foundation and identifying novelty gaps before writing the first line of code.

---

### Selected projects

**[AirWatch India](https://github.com/arnav-rishi/Airwatch-ET)** — Built for the ET AI Hackathon 2026. The problem: given live pollution hotspot data, which specific facility should an inspector visit today?

The answer can't come from an LLM guessing a zone name. So the system maintains a registry of 7,900+ registered emission sources — industries, construction sites, diesel fleet depots, waste sites — with real coordinates across 82 Indian cities, seeded from OpenStreetMap via the Overpass API. Each source is scored against the hotspot on five components: proximity, atmospheric transport (Gaussian plume dispersion with Briggs urban σ curves and Pasquill-Gifford stability class derived from live wind and insolation), source-category match, dispatchability, and hotspot severity. The LLM is called last — handed a ranked shortlist with component scores it cannot change — and writes the dispatch narrative. Signal to dispatch-ready in 30–60 seconds. For a Delhi hotspot, the system narrows a 213-source search space to 5 candidates (42.6×).

Worth mentioning: mid-build we discovered 80 of 84 WAQI city feeds were serving stale data — one was 1,710 days old. Those readings were driving the enforcement ranking. Switched to OpenAQ v3 (timestamped, CPCB scale), added staleness gating at three layers, and the API now returns an honest 503 when nothing is fresh rather than fabricating urgency from a 2021 signal. The demo numbers look less dramatic; the data is real.

`FastAPI` `Python 3.11` `React` `Tailwind CSS v4` `Leaflet.js` `Azure OpenAI` `OpenAQ v3` `NASA FIRMS` `OpenStreetMap` · 162 tests · GitHub Actions CI

---

**[Eco-Loop Building Agent](https://github.com/darkhorse0204/eco-loop)** — Built for the Honeywell Eco-Loop hackathon. EnergyPlus (the building physics simulator used by real engineers) controlled in a live closed loop by Llama 3.1 8B running locally via Ollama. Every 15 minutes the model reads the building's sensors — zone temperatures, CO₂, occupancy, outdoor conditions, current electricity price and grid carbon intensity — and calls `set_hvac_setpoints(cooling, heating, reason)`. A hard guardrail clamps its output to the comfort band before anything reaches EnergyPlus, so comfort is safe regardless of what the model says.

Two-week simulated Tampa office run: AC electricity −15.1%, cooling energy −22.2%, bill −8.7% (more than the energy saving — the AI saves roughly twice as much during the expensive 4–9pm peak as off-peak), carbon −6.4%. Comfort (PMV) and CO₂ both held at 100% throughout. Verified against a hand-tuned rule controller in an ablation study: the LLM wins on every metric, about 45% more total savings. ~1,000 decision points became 171 actual LLM calls via regime-based caching. The fallback controller ran without issue when the AI stalled once during testing.

Building controls are also exposed as 6 MCP tools for anything that wants to plug in a different agent.

`Python` `EnergyPlus 25.1.0 Runtime API` `Ollama (Llama 3.1 8B)` `Streamlit` `MCP`

---

**[Enterprise AI Copilot for Google Sheets](https://github.com/darkhorse0204/sheets-ai-pipeline)** 

A production-grade AI copilot built entirely on Google Apps Script and Gemini. Instead of a naive chat wrapper, requests run through a strict layered pipeline: Context Builder → Planner → User Approval Workflow → 7 Specialist Agents (via ReAct loops) → 4-layer Formula Verification.

The system builds "deep context" by analyzing the active spreadsheet's schema and formatting before generating a structured plan. The planner's output is blocked on user approval in the custom HTML/CSS sidebar. If approved, a Step Executor dispatches tasks to the specialized agents. Critically, it includes an Enterprise module that handles rate limiting, cost tracking, a dry-run capability, and a full undo stack for safe transactions. If a generated formula fails the 4-layer verification, the verifier automatically constructs a retry prompt with the error trace and sends it back to the Gemini API.

`JavaScript` `Google Apps Script` `Gemini API` `HTML/CSS`

---

### Tech

Python for most things — FastAPI for APIs, NumPy/scikit-learn for classical ML, PyTorch when there's a model. React + TypeScript (Vite, Tailwind CSS) when there's a frontend. Azure OpenAI and Ollama depending on whether the system needs to run offline. MCP when tools need a standard interface.

Testing with pytest. GitHub Actions for CI. Leaflet.js for geospatial work. EnergyPlus for building physics.

---

### Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=darkhorse0204&show_icons=true&hide_border=true&count_private=true&theme=github_dark)

---

### Contact

[LinkedIn](https://www.linkedin.com/in/ansh-jerath-a25412214) · jerathansh@gmail.com
