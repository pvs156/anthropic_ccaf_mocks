# Claude Certified Architect – Foundations (CCA-F) Practice Mocks

Six full-length, self-contained practice mock exams for the **Claude Certified Architect – Foundations (CCA-F)** certification. Each is a single offline HTML file — no server, no build step, no internet required.

## Contents

| File | Batch |
| --- | --- |
| [`mocks/index.html`](mocks/index.html) | Launcher for all six |
| `mocks/CCA-F_Mock_Exam_Batch1.html` | Batch 1 |
| `mocks/CCA-F_Mock_Exam_Batch2.html` | Batch 2 |
| `mocks/CCA-F_Mock_Exam_Batch3.html` | Batch 3 |
| `mocks/CCA-F_Mock_Exam_Batch4.html` | Batch 4 |
| `mocks/CCA-F_Mock_Exam_Batch5.html` | Batch 5 |
| `mocks/CCA-F_Mock_Exam_Batch6.html` | Batch 6 |

**6 mocks × 60 questions = 360 practice questions.**

Also included: [`CCAR-F_tips_and_tricks.md`](CCAR-F_tips_and_tricks.md) — a study guide covering the exam domains, weightings, granular objectives, test-day tactics, and common traps.

## How to use

Open `mocks/index.html` in any browser and pick a batch — or open any batch file directly. Each mock:

- Hides your score while you take it.
- Runs a **pausable 2-hour timer** (auto-submits at zero).
- Shows results **only at the end**: raw score, an approximate scaled score against the ~720/1000 pass line, a per-domain breakdown, and a full question-by-question review with the correct answer and explanation for each item.
- Includes a question palette (jump to any question), flag-for-review, clear-answer, and an unanswered-questions warning before final submission.

Everything runs client-side, so you can also use it offline or host it with GitHub Pages (enable Pages on the `main` branch and point at `/mocks`).

## Exam structure these mocks target

The CCA-F exam is 60 questions in 120 minutes across five domains. Each mock mirrors that shape:

| Domain | Focus | Questions per mock |
| --- | --- | --- |
| 1 | Agentic Architecture & Orchestration | 16 |
| 2 | Tool Design & MCP Integration | 11 |
| 3 | Claude Code Configuration & Workflows | 12 |
| 4 | Prompt Engineering & Structured Output | 12 |
| 5 | Context Management & Reliability | 9 |

## Suggested study approach

1. Take one mock cold as a timed diagnostic.
2. After each attempt, log every miss: **date · domain · why you missed it**.
3. Space the remaining mocks out across your prep, re-answering past misses between attempts.
4. The day before the real exam, do a speed pass over your accumulated miss-log rather than cramming new material.

## Disclaimer

These are **independent practice materials** for self-study and are not affiliated with, endorsed by, or produced by Anthropic. Question content was compiled for personal exam preparation. Verify current exam objectives against Anthropic's official CCA-F exam guide.
