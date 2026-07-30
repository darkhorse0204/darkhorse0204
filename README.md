## hey, I'm Ansh

I'm a final year CS student at VIT Vellore. I like building systems where AI handles the fuzzy decision support while physics and hard math make the actual calls.

### What I'm working on
* **Samsung PRISM :** Wrapping up a multimodal framework to detect AI generated content. The text detector hits 95% accuracy on HC3.
* **CAPS-FCL:** Early research phase for an IoT and computer vision waste segregation system.

### Selected projects

**[AirWatch India](https://github.com/arnav-rishi/Airwatch-ET)** 
Built for the ET AI Hackathon. Takes live pollution hotspot data and figures out exactly which facility an inspector should visit. Instead of an LLM guessing, it scores 7,900+ real emission sources using a Gaussian plume dispersion model with live wind data. 
*(Fun fact: we caught that 80 out of 84 WAQI city feeds were serving years-old data during this build. Switched to OpenAQ v3 with strict staleness checks so the API fails honestly rather than faking urgency).*

**[Eco-Loop Building Agent](https://github.com/darkhorse0204/eco-loop)** 
Honeywell Eco-Loop hackathon project. Uses a local Llama 3.1 8B model to control EnergyPlus (a building physics simulator) in a live closed loop. It cut cooling energy by 22% and the total bill by 9% in a two week simulated run, while keeping human comfort levels perfect. 

**[Enterprise AI Copilot for Google Sheets](https://github.com/darkhorse0204/sheets-ai-pipeline)** 
A production grade AI copilot built natively on Google Apps Script and Gemini. Uses a strict pipeline (Context Builder to Planner to 7 Specialist Agents to Formula Verification) instead of a basic chat wrapper. Includes full undo stacks, cost tracking, and dry runs.

### Tech stack
Python (FastAPI, PyTorch, scikit-learn), React (TypeScript, Vite, Tailwind), Azure OpenAI, Ollama, MCP.

### Contact
[LinkedIn](https://www.linkedin.com/in/ansh-jerath-a25412214) | jerathansh@gmail.com
