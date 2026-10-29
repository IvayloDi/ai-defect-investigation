# Defect summary

Closed 9 Oct 2026. I counted only cases I had finished. This is not a ranking.

## Register

| ID | What I was checking | How I classified it | Severity | Priority | Status |
|---|---|---|---|---|---|
| [DEF-001](../defects/DEF-001-Instruction-Following.md) | Does "exactly three" stay three? | No defect on four products | — | — | Closed, no defect |
| [DEF-002](../defects/DEF-002-Context-Loss.md) | Does a short chat keep a language and a reference code? | No defect on four products | — | — | Closed, no defect |
| [DEF-003](../defects/DEF-003-Hallucinated-Facts.md) | Does a company question invent records? | No defect on four products | — | — | Closed, no defect |
| [DEF-004](../defects/DEF-004-Ambiguous-Prompt.md) | Is "Should I use Java?" a defect? | Expected AI Behaviour | — | — | Closed, Expected AI Behaviour |
| [DEF-005](../defects/DEF-005-Inconsistent-Behavior.md) | Do fresh chats disagree on a stable fact? | No defect on four products | — | — | Closed, no defect |

## Where the notes are

| Case | Note | Prompts |
|---|---|---|
| DEF-001 | [investigation-001](../investigations/investigation-001.md) | [P-001](../test-data/prompts.md#def-001-instruction-following) |
| DEF-002 | In the ticket | [P-002](../test-data/prompts.md#def-002-context) |
| DEF-003 | [investigation-002](../investigations/investigation-002.md) | [P-003](../test-data/prompts.md#def-003-hallucinated-facts) |
| DEF-004 | [investigation-003](../investigations/investigation-003.md) | [P-004](../test-data/prompts.md#def-004-ambiguous-prompt) |
| DEF-005 | In the ticket | [P-005](../test-data/prompts.md#def-005-inconsistent-behavior) |

## Counts

DEF-004 is the expected-behaviour close. The other four are closed with no defect. I did not count either of those as a product defect.

| | n |
|---|---|
| Product defect | 0 |
| Known limitation | 0 |
| Expected behaviour | 1 |
| Prompt sensitivity as the main label | 0 |
| Closed, no defect | 4 |

Nothing left open. No partials.

| Severity | n |
|---|---|
| Critical | 0 |
| High | 0 |
| Medium | 0 |
| Low | 0 |

## Pass / fail by prompt

"Not run" means I did not send that prompt on that product. I am not picking a best or worst product from this table.

| Prompt | ChatGPT | Claude | Gemini | Perplexity |
|---|---|---|---|---|
| P-001-A | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass |
| P-001-C | Pass | Pass | Pass | Pass |
| P-002 recall | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass |
| P-003-A | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass |
| P-003-B | Not run | Not run | Not run | Pass |
| P-003-C | Not run | Not run | Not run | Pass |
| P-004-A | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass |
| P-004-B | Pass | Pass | Pass | Pass |
| P-005-A | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass | Pass, Pass, Pass |
