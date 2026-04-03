# Project OS — CVTest1
# Save as: CVTest1/.agent/CLAUDE.md
# Read by: Antigravity, Kilo Code, Claude Code, any ECC-compatible tool

## Project
Job application automation pipeline. See CLAUDE.md in project root for full context.
Building: CV generator, JD analyzer, cover letter generator, DOCX formatter.

## Planning Rules
- ALWAYS read root CLAUDE.md before any task
- Break goal into micro-tasks (2–5 min each, max 5 per session) before writing ANY code
- State function signatures and data flow before implementation begins
- Single focused planning phase — do not re-plan or repeat
- Wait for explicit approval before executing

## Coding Rules
- Write FAILING TEST first — no implementation before a failing test exists (TDD iron rule)
- Max one file changed per micro-task
- All LLM calls via `models/llm_router.py` — never call SDKs directly from generators
- All structured data via `models/schemas.py` dataclasses — no raw dicts
- JSON from LLMs: always try/except, strip ``` fences before json.loads()
- Commit after each verified micro-task

## Model Selection (in Kilo)
- Session 1–2 (ats_rules, jd_analyzer): Gemini 3.1 Pro Preview
- Session 3 (llm_router): Qwen 3.6 Plus
- Session 4 (search.py): GLM-5
- Sessions 5–8 (generators): Gemini 3.1 Pro Preview
- Session 7 (cv_arbiter): Claude Opus 4.6 — Claude Code CLI interactive ONLY
- Sessions 9–10 (docx, CLI): Qwen 3.6 Plus

## Review Rules
- After each task: does output match spec? Do tests pass?
- For generators: run against jds/bos_role02_ai_sw_engineer.txt as smoke test
- Fix before moving to next task

## STOP CONDITIONS — stop and notify if:
- Planning for more than 60 seconds without a test written
- Writing multiple files in one pass
- Calling Anthropic API for Opus (Opus = interactive only, never API in pipeline)
- Context fill above 40%
