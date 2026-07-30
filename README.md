## hey, I'm Ansh

I'm a final year IT student at VIT Vellore. I like building systems where AI handles the fuzzy decision support while physics and hard math make the actual calls.

### What I'm working on

Right now I'm wrapping up a cost aware framework for Samsung PRISM that detects AI generated text, images, audio, and video in data pipelines. The text detector is already done and hits about 95% accuracy on HC3. The fusion engine for all four modalities is running too, just waiting on a good labeled dataset to get the final benchmark numbers. I'm keeping the project status doc updated with what's actually measured instead of making wild claims.

I'm also doing some early research for CAPS-FCL. It's a waste segregation system using computer vision, IoT sensor fusion, and federated learning. I've been reading through a ton of literature and patents to figure out what's actually novel before I start writing code.

### Selected projects

**[AirWatch India](https://github.com/arnav-rishi/Airwatch-ET)** 
I built this for the ET AI Hackathon 2026. The goal was to take live pollution hotspot data and figure out exactly which facility an inspector should visit that day.

I didn't want to just ask an LLM to guess a zone name. So the system keeps a registry of over 7,900 emission sources across 82 Indian cities using OpenStreetMap data. It scores each source against the hotspot based on proximity, atmospheric transport (using a Gaussian plume dispersion model with live wind data), category match, and a few other things. The LLM only comes in at the very end to write a dispatch narrative based on a ranked list it isn't allowed to change. It takes about 30 to 60 seconds to go from signal to a dispatch ready report.

One fun thing: while building it we realized 80 out of 84 WAQI city feeds were serving super stale data. One of them was almost five years old. We ended up switching to OpenAQ v3, adding strict staleness checks, and making the API fail honestly instead of faking urgency with old data. The demo numbers look less crazy now but at least they are real.

**[Eco-Loop Building Agent](https://github.com/darkhorse0204/eco-loop)** 
This was for the Honeywell Eco-Loop hackathon. It uses a local Llama 3.1 8B model to control EnergyPlus, which is a building physics simulator. Every 15 minutes the model checks the building sensors like temperature, CO2, and occupancy, along with electricity prices. Then it sets the HVAC setpoints. There is a hard safety guardrail that keeps the AI's choices within a strict comfort band so things don't go off the rails.

In a two week simulated run for a Tampa office, it cut cooling energy by 22% and the total bill by about 9%. It actually saves more money than energy because the AI learns to cut back during peak pricing hours. Comfort and CO2 levels stayed perfect the whole time. I compared it to a hand tuned rule controller and the LLM saved about 45% more overall. The controls are also exposed as MCP tools in case someone wants to plug in a different agent.

**[Enterprise AI Copilot for Google Sheets](https://github.com/darkhorse0204/sheets-ai-pipeline)** 
This is a production grade AI copilot built natively on Google Apps Script and Gemini. Instead of just a basic chat interface, it runs requests through a strict pipeline: Context Builder to Planner to User Approval to 7 Specialist Agents to a 4 layer Formula Verification.

It scans the spreadsheet's schema to build deep context and plans out the steps. The user has to approve the plan in the sidebar before it executes. I also built an enterprise module that handles rate limiting, cost tracking, and dry runs, plus a full undo stack so it's safe to use. If a formula fails, the verifier automatically catches the error trace and prompts Gemini to fix it.

### Tech stack

I mostly use Python with FastAPI for backend stuff, and PyTorch or scikit-learn when working with models. For the frontend I usually go with React, TypeScript, Vite, and Tailwind. I use Azure OpenAI or Ollama depending on if it needs to run locally, and MCP for tool interfaces. 

### Contact

[LinkedIn](https://www.linkedin.com/in/ansh-jerath-a25412214)
Email: jerathansh@gmail.com
