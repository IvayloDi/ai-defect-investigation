# AI Defect Investigation

Five defect cases on the free web chats of ChatGPT, Claude, Gemini, and Perplexity. Each case asks whether a user-visible failure is a product defect. The products are not scored and they are not ranked.

Executed on 9 October 2026. Four cases closed with no defect. DEF-004 closed as Expected AI Behaviour.

The companion project, AI Assistant Comparative Testing, scores the same four products on 20 prompts. This repository is the defect investigation: one claim per ticket, the runs that support it, and the close.

## Goal

Reproduce a claim on the public web chat, classify it, and close it. A pass is written down. A case that does not fail is not turned into a defect.

## Scope

- Products: ChatGPT free at https://chatgpt.com/ (mode Think), Claude free at https://claude.ai/new (Sonnet 5.5 Medium), Gemini at https://gemini.google.com/app (Flash-Lite, not signed in), and Perplexity at https://www.perplexity.ai/ (Search).
- Interface: the public web chat. One new conversation per run.
- In scope: a fixed item count, a short chat that must keep two facts, a company question that must not invent records, an underspecified recommendation, and a stable fact sent in fresh chats.
- Out of scope: model ranking, a failure rate from three runs, paid plans, API runs, file uploads, and changes to account settings.

## Method

Classification, severity, and priority are decided in [standards/defect-rules.md](standards/defect-rules.md) before a ticket is closed. The prompt text is only in [test-data/prompts.md](test-data/prompts.md).

Each claim is three new chats. Regenerate is not one of the three. A second prompt, when it was sent, is recorded separately. Screenshots are in [screenshots/](screenshots/). Names, email addresses, and avatars are masked. Cookies and tokens are not stored.

## Case index

| ID | Category | What is checked | Result |
| --- | --- | --- | --- |
| [DEF-001](defects/DEF-001-Instruction-Following.md) | Instruction following | A request for exactly three advantages, including when each item must also be explained | Three items on every run. Closed, no defect. |
| [DEF-002](defects/DEF-002-Context-Loss.md) | Context | Python and the code QA-NEEDLE-8841, recalled after five unrelated turns | Both facts exact on all twelve chats. Closed, no defect. |
| [DEF-003](defects/DEF-003-Hallucinated-Facts.md) | Hallucination | No invented address, number, director, year, or revenue for Zindlewick Craymoor Ltd | The company was not found. No invented record. Closed, no defect. |
| [DEF-004](defects/DEF-004-Ambiguous-Prompt.md) | Ambiguous request | "Should I use Java?" with no system, team, or goal | Conditional recommendation. Closed as Expected AI Behaviour. |
| [DEF-005](defects/DEF-005-Inconsistent-Behavior.md) | Consistency | The capital of Australia, asked in fresh chats | Canberra on all twelve chats. Closed, no defect. |

DEF-001, DEF-003, and DEF-004 have a separate note where a second prompt was checked: [investigation-001](investigations/investigation-001.md), [investigation-002](investigations/investigation-002.md), and [investigation-003](investigations/investigation-003.md). DEF-002 and DEF-005 stay in the ticket.

## Repository map

- [standards/defect-rules.md](standards/defect-rules.md) — classification, severity, and priority
- [test-data/prompts.md](test-data/prompts.md) — the prompt text that was sent
- [defects/](defects/) — five tickets. Each one has steps, the result, and the evidence
- [investigations/](investigations/) — the boundary notes for DEF-001, DEF-003, and DEF-004
- [reports/Defect_Summary.md](reports/Defect_Summary.md) — register and pass/fail by prompt
- [reports/Risk_Assessment.md](reports/Risk_Assessment.md) — what would have been at risk if a run had failed
- [reports/Lessons_Learned.md](reports/Lessons_Learned.md) — what the runs showed
- [screenshots/](screenshots/) — evidence, named by defect, product, prompt, and run
