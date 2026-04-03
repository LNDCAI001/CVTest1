# CVTest1 — Job Application Automation Pipeline
# CLAUDE.md — Project Memory (FINAL — April 2026)

**Owner:** Caide Lander | Seoul, South Korea
**Repo:** github.com/LNDCAI001/CVTest1
**Path:** C:\Users\Caide Lander\Documents\CV and Jobs\CVTest1

---

## Who I Am

Caide Lander — BEng Mechatronics (First Class, UCT, GPA 68.72, March 2025). Dual British/South African. Native English speaker (British). Seoul, tourist visa. ADHD — passive task surfacing only, no over-engineering.

**UCT projects:**
- LQR planetary lander: 99.8% Monte Carlo success, real-time C++ control
- ANN/CNN classifier: ~98% accuracy, Python/NumPy, multi-class
- CUDA/HPC: parallel kernel implementation, memory tiling, GPU vs CPU analysis
- STM32 PCB: self-soldered ARM Cortex-M, bare-metal C, I2C/SPI/UART from scratch
- Autonomous maze robot: embedded C, sensor fusion, real-time RTOS path planning
- Blockchain RBAC FYP: Solidity, gas optimization, 2FA evolution, security audit
- Hornbill IoT: edge sensors, Python data pipeline, thermal control

**FirstRand:**
- GEM: Java, live electronic trading, FixHub threshold monitor
- ERM: Python ETL (2–5 hrs/week saved/team), Monte Carlo risk, PowerBI, LLM doc summarization, SAS-to-Python migration

**Other:** Dale Carnegie comms, UCT tutoring, DeepSeek autonomous agent, RAG chatbot, knife-making business

---

## Priority Applications

| Priority | Role | Deadline |
|----------|------|----------|
| P0 | BOS Semi Role 02 — AI SW Engineer (신입) | **NOW** |
| P0 | BOS Semi Role 13 — Technical Writer | **NOW** |
| P1 | BOS Semi Role 01-1 — ML Runtime (신입) | This week |
| P1 | BOS Semi Role 01 — Embedded SW | This week |
| P2 | CERN BE-CEM-MRO-2026-12 | Ongoing |
| P2 | CERN SY-ABT-BTE-2026-61 | Ongoing |
| P3 | IFRoS | April 26 |

---

## Full Dev Stack

**Google Antigravity IDE** — agent-first development environment (free).
**Kilo Code** — model router extension inside Antigravity. 60+ providers, parallel agents.
**Claude Code CLI** — Opus 4.6 interactive sessions (Pro subscription, zero API cost).
**ECC + Superpowers** — methodology layer in `.agent/`. Disciplines Gemini 3.1 Pro, enforces TDD.

---

## Model Routing — Final

### Intelligence Index (ArtificialAnalysis April 2026)
| Model | Index | Notes |
|-------|-------|-------|
| Gemini 3.1 Pro Preview | **57** | Highest — but requires ECC+Superpowers discipline |
| Claude Opus 4.6 | **53** | Best agentic coder, CLI only |
| GLM-5 | **50** | #1 open weights overall |
| Qwen 3.6 Plus | ~45 | Free on Kilo, 1M context, disciplined |
| DeepSeek V3.2 | **42** | Elite reasoning/math, free on Nvidia |

### Assignment Table

| Task | Model | Access | Cost |
|------|-------|--------|------|
| Architecture decisions, CV arbiter, hard review | **Opus 4.6** | Claude Code CLI interactive only — NEVER via API | $0 |
| CV Thread A, JD analysis, cover letters, masters | **Sonnet 4.6** | Anthropic API | ~$0.04/gen |
| Main implementation coder (pipeline code) | **Gemini 3.1 Pro Preview + ECC+SP** | Antigravity Agent Manager | Free (rate-limited) |
| Bulk implementation, long-context code tasks | **Qwen 3.6 Plus** | Kilo Code (completely free) | $0 |
| Fast scaffolding, test skeletons | **GLM-5** | Kilo → Nvidia `z-ai/glm5` | $0 |
| Reasoning, math-heavy logic, research | **DeepSeek V3.2** | Kilo → Nvidia `deepseek-ai/deepseek-v3.2` | $0 |
| Open-weights reasoning/agents backup | **Gemma 4 31B** | Kilo → Nvidia `google/gemma-4-31b-it` | $0 |
| CV Threads B+C, resume skills | **Gemini CLI** | `gemini` command (free tier) | $0 |
| Korean JD translation | **Gemini Flash** | Google GenAI API | ~free |
| Deep research backup | **Kimi K2.5** | Kilo → Nvidia `moonshotai/kimi-k2.5` | $0 |
| True last resort | **DeepSeek V3.2** | OpenRouter | ~$0.70/M |

**RULES:**
- Opus is NEVER called via API inside the Python pipeline. Arbiter step = interactive Claude Code session.
- Gemini 3.1 Pro Preview builds the pipeline code. Sonnet 4.6 API generates candidate-facing outputs.
- Qwen 3.6 Plus handles bulk implementation when Gemini rate limits hit.
- ECC+Superpowers MUST be active for Gemini 3.1 Pro — without it, it overthinks and wastes tokens.

### SDK Patterns (NO LangChain)
```python
import anthropic
sonnet_client = anthropic.Anthropic()  # ANTHROPIC_API_KEY — Sonnet only

from google import genai
gemini_api_client = genai.Client(api_key=os.environ["GOOGLE_AI_KEY"])  # Flash, translation

from openai import OpenAI
nvidia_client = OpenAI(
    base_url="https://integrate.api.nvidia.com/v1",
    api_key=os.environ["NVIDIA_API_KEY"]  # Free models
)
openrouter_client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key=os.environ["OPENROUTER_KEY"]  # Fallback only
)

import subprocess
def gemini_cli_skill(prompt: str) -> str:
    """Invoke Gemini CLI with resume skills prefix."""
    result = subprocess.run(["gemini", prompt], capture_output=True, text=True, timeout=120)
    return result.stdout
```

### Confirmed Nvidia Model IDs (curl verified April 2026)
```
deepseek-ai/deepseek-v3.2          # primary reasoning/code
z-ai/glm5                          # fast scaffolding
moonshotai/kimi-k2.5               # research, 256K ctx
moonshotai/kimi-k2-thinking        # reasoning mode
google/gemma-4-31b-it              # open-weights backup
qwen/qwen3-coder-480b-a35b-instruct
qwen/qwen3.5-397b-a17b
mistralai/devstral-2-123b-instruct-2512
nvidia/nemotron-3-super-120b-a12b
minimaxai/minimax-m2.5
```

---

## CV Generation Architecture

```
JD + Master CV
        │
        ├─ THREAD A: Sonnet 4.6 API
        │  + Claude skills: cv-writer, resume-ats-optimizer,
        │    resume-formatter, resume-optimization
        │  → Draft A
        │
        ├─ THREAD B: Gemini CLI
        │  + Skills: Resume Tailor, ATS Optimizer,
        │    Bullet Writer, Quantifier
        │  → Draft B
        │
        └─ THREAD C: Gemini CLI
           + Skills: Tech Resume Optimizer,
             Section Builder
           → Draft C

A + B + C → Opus 4.6 (Claude Code interactive session)
  → Final synthesized CV JSON → docx_formatter.py → .docx
```

**Gemini skill invocation:**
```bash
gemini "Use Resume Tailor skill. Role: [role] at BOS Semiconductors. JD requirements: [key JD bullets]. My background: [relevant achievements]. Output 6 achievement bullets."
gemini "Use Resume ATS Optimizer skill. Check these bullets. Missing keywords: [list]. Suggest insertions."
gemini "Use Resume Quantifier skill. Add defensible metrics: [bullets]"
```

---

## BOS Semiconductors Context

**Products:** Eagle-N (NPU/AI accelerator), Eagle-A (automotive SoC). Chiplet, leading-node process. ADAS/IVI/Physical AI. 200+ R&D staff, Vietnam subsidiary, 4 years old.

**Tech:** ARM/RISC-V, Linux/Android/QNX/Zephyr, C/C++, Python, PyTorch/TensorFlow, TVM/MLIR, NPU runtime, ASPICE, ISO 26262.

**Advantages:** Seoul-based (no sponsorship), native English (rare), met at Yonsei Job Fair (warm lead), 신입 roles open.

### Role Strategy

| Role | Fit | Key Angle |
|------|-----|-----------|
| 02 AI SW Engineer | **Strong** | ANN/CNN ~98%, CUDA kernels, LLM tooling, hardware-aware |
| 13 Technical Writer | **Strong** | Native English + BEng = rare; can write datasheets with domain depth |
| 01-1 ML Runtime | **Good** | C/C++, ARM, parallel computing, latency-aware |
| 01 Embedded SW | **Good** | STM32 bare-metal, peripheral drivers, RTOS |
| 06 SoC Solution FW | **Medium** | Python automation, embedded debug |
| 14 ASPICE | **Medium** | Technical comm, structured docs, V-model |

---

## Current State

### ✅ P0 Complete (do not rewrite)
`requirements.txt`, `.gitignore`, `.env.example`, `config/variants.yaml` (7 tracks), `config/master_cv.md`, `config/playbook.md`, `knowledge/achievements.yaml` (~25 STAR entries), `prompts/system_cv.py`, `prompts/system_cover_letter.py`, `models/schemas.py`

### 🔲 P1 Sessions

| # | File | Model in Kilo |
|---|------|--------------|
| 1 | `config/ats_rules.yaml` | Gemini 3.1 Pro + ECC |
| 2 | `prompts/jd_analyzer.py` + `models/cost_tracker.py` | Gemini 3.1 Pro + ECC |
| 3 | `models/llm_router.py` | Qwen 3.6 Plus |
| 4 | `knowledge/search.py` | GLM-5 |
| 5 | `generators/cv_generator.py` | Gemini 3.1 Pro |
| 6 | `generators/cv_generator_gemini.py` | Gemini 3.1 Pro |
| 7 | `generators/cv_arbiter.py` | **Opus interactive** |
| 8 | `generators/cover_letter_generator.py` | Gemini 3.1 Pro |
| 9 | `generators/docx_formatter.py` | Qwen 3.6 Plus |
| 10 | `generate.py` | Qwen 3.6 Plus |

### 🔲 P2 (after P1 end-to-end)
`knowledge/ingest.py`, `tracker/tracker.py`, `generators/masters_generator.py`

### 🔲 Phase 2
Scraping MCPs, Todoist (`mcp__c880051d-*` connected), Telegram bot

---

## Key Paths

```
# READ ONLY source data
C:\Users\Caide Lander\Documents\CV and Jobs\Useful Uploads\Master_CV_Data_3.1.md
C:\Users\Caide Lander\Documents\CV and Jobs\Useful Uploads\CV_Generation_Playbook.md
C:\Users\Caide Lander\Documents\CV and Jobs\Useful Uploads\Caide_Application_Tracker.xlsx

# Claude skills (load into Thread A system prompt)
C:\Users\Caide Lander\.claude\skills\cv-writer\SKILL.md
C:\Users\Caide Lander\.claude\skills\resume-ats-optimizer\SKILL.md
C:\Users\Caide Lander\.claude\skills\resume-formatter\SKILL.md
C:\Users\Caide Lander\.claude\skills\resume-optimization\SKILL.md

# JD files
CVTest1\jds\bos_role02_ai_sw_engineer.txt
CVTest1\jds\bos_role13_technical_writer.txt
CVTest1\jds\bos_role01_1_ml_runtime.txt
CVTest1\jds\bos_role01_embedded_sw.txt
```

---

## Environment

```
ANTHROPIC_API_KEY=sk-ant-...   # Sonnet 4.6 only — Opus via Claude Code CLI
GOOGLE_AI_KEY=...              # Gemini Flash + CLI resume skills
NVIDIA_API_KEY=...             # Free: DeepSeek V3.2, GLM-5, Gemma 4, Kimi, Qwen
OPENROUTER_KEY=sk-or-...      # Fallback only
```

---

## Coding Standards
- Python 3.11+, type hints on all functions
- All structured data → `models/schemas.py` dataclasses, no raw dicts
- All LLM calls → `LLMRouter` — never call SDKs from generators directly
- JSON from LLMs → always `try/except`, strip fences before `json.loads()`
- Log every generation: provider, model, tokens, cost_usd, company, timestamp
- Track IDs always from `config/variants.yaml`, never hardcoded
- ATS rules enforced in `docx_formatter.py` — prompts guide content only

## ATS / DOCX Rules
Single column, no tables/text boxes/graphics/headers/footers. Calibri 11pt body / 14pt name / 12pt headers. 0.5" margins. Filename: `Caide_Lander_CV_[Company].docx`. Max 1 page.

## GSD Discipline
Discovery → Planning (confirm before writing) → Execution (TDD: failing test first) → Verification (real output, not "compiled"). Stop at 40% context fill.
