# Claude Certified Architect – Foundations (CCAR-F)
### Tips, Tricks & Study Guide

A practical prep guide for Anthropic's CCAR-F exam. Built from the exam blueprint, the domain weightings, and prep advice from people who've passed it.

---

## The exam at a glance

- **Format:** 60 scenario-based multiple-choice questions
- **Time:** 120 minutes (about 2 minutes per question)
- **Style:** Closed-book, proctored (webcam, no notes, no tabs, no Claude)
- **What it tests:** Architectural judgment, not recall. Most questions drop you into a system that's already going wrong and ask which of four fixes actually holds up. Two options usually look reasonable.

The single most important mindset shift: **this is not a "know the API" exam.** It rewards people who've built and broken real agentic systems and can reason about tradeoffs.

---

## The five domains (and roughly how they're weighted)

| Domain | Weight | What it really covers |
|---|---|---|
| Agentic Architecture & Orchestration | ~27% | Single-agent vs. multi-agent, coordinator-worker patterns, parallel vs. sequential pipelines, subagent delegation, state persistence and resumption |
| Prompt Engineering & Structured Output | ~20% | Tool use with JSON schema, `tool_choice`, prefilled responses, extraction schemas, few-shot design, handling truncation |
| Claude Code Configuration & Workflows | ~20% | CLAUDE.md vs. rules vs. Skills vs. hooks vs. settings, CI/CD invocation flags, review configs, `context: fork` |
| Tool Design & MCP Integration | ~18% | MCP resources vs. tools, server scope and auth, writing tool descriptions that prevent misrouting, tool distribution across subagents |
| Context Management & Reliability | ~15% | Context window optimization, subagent isolation, scratchpad files, human-in-the-loop routing, sync vs. batch API |

Weightings are approximate — treat Agentic Architecture as the heaviest and study it first.

---

## What actually gets tested (the granular objectives)

### Agentic architecture & orchestration
- Configuring agentic loops to emit **multiple tool calls in a single turn** for parallel execution
- Choosing **goal-oriented vs. procedural** subagent instructions (and knowing when each wins)
- Deciding when a task **warrants a subagent vs. a single call**
- Designing **state persistence** so a multi-agent pipeline can resume after interruption without redoing finished work
- Comparing **coordinator-worker, parallel, and sequential** patterns against coverage, latency, and reliability needs
- **Dynamically decomposing** tasks as new info is discovered, rather than running a fixed sequence
- Selecting the right **review architecture** (plan mode, direct execution, multi-phase) based on risk and approval needs
- Diagnosing **misconfigured subagent spawning** (missing tool permissions, wrong AgentDefinition params, broken wiring)

### Tool design & MCP
- **Resources vs. tools:** expose server content as resources to cut exploratory tool calls
- Integrating MCP servers: **server scope, auth via env variable expansion, verifying tool discovery**
- Writing **tool descriptions** that clearly separate purpose, inputs, and boundaries so the model doesn't misroute
- **Distributing tools** so each subagent only gets what its role needs
- Configuring **`tool_choice`** to guarantee invocation, and sequencing multi-tool workflows so prerequisites resolve first

### Claude Code
- Picking the right config mechanism: **CLAUDE.md, `.claude/rules/` with globs, Skills, hooks, or settings permissions** — based on the type of guidance and when it should apply
- **`context: fork`** for Skills and slash commands that should run in an isolated subagent context
- Non-interactive CI/CD invocation: **permission modes, cost and turn limits** to prevent runaway runs
- Designing **review configs** that load the right standards and produce structured output
- Systematic codebase exploration with **Grep, Glob, Read** while managing the context window

### Prompt engineering & structured output
- Choosing the **structured output method:** tool use with JSON schema vs. prompt-based vs. prefilled
- Designing **extraction schemas** with optional/nullable fields and enums so the model represents missing data instead of fabricating
- **Resolving truncation** by splitting into scoped calls and merging, rather than cranking `max_tokens`
- **Specialized review passes** that separate concerns (security, business logic, API design) into focused prompts
- Defining **inclusion/exclusion boundaries** so the model doesn't generate findings where it's unreliable

### Context management & reliability
- **Context window optimization:** summarization, sliding windows, structured state objects, selective retention
- **Subagent isolation and scratchpad files** to sustain coherent work across sessions that exceed limits
- **Human review routing** based on confidence scores and field-level ambiguity, not random sampling
- **Sync Messages API vs. async Message Batches API** based on latency and blocking needs

---

## Test-day tactics

- **Two minutes per question.** Don't over-invest early. Flag and move on.
- **Eliminate the two "reasonable-looking" wrong answers first.** Most questions have two plausible distractors. The real skill is spotting which plausible option breaks under production constraints (latency, cost, reliability, auditability).
- **When two answers seem equally right, pick the simpler architecture.** The boring, plainer design is usually the intended answer. Over-engineering is a common trap.
- **Watch for "human-in-the-loop" cues.** If a scenario involves high risk, irreversibility, or ambiguity, the answer often involves keeping a human in the loop rather than fully trusting the model.
- **Read for the constraint.** Every scenario has a hidden priority — latency, cost, reliability, coverage. Identify it before comparing options.
- **Set up your space early.** Clear desk, working webcam, stable connection. Proctoring flags anything that looks off, so remove the friction before you start.

---

## Common traps

- Choosing the **cleverest** solution over the one that survives real traffic
- Reaching for **more subagents** when a single call would do
- Increasing **`max_tokens`** instead of splitting a task when output truncates
- Treating **MCP tools** as the answer when a **resource** is the more efficient abstraction
- Assuming **state survives a restart** when it hasn't been designed to
- Giving subagents **more tools than their role needs**, which increases decision complexity and misfires

---

## One-line summary

Prompt engineering gets you a good demo. Architecture gets you a system that's still reliable, auditable, and cost-sensible six months in with real users hitting it. The exam is built to tell the difference.

Good luck.
