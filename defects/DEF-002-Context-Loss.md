# DEF-002 Context Loss

| Field | Value |
|---|---|
| Status | Closed, no defect |
| Category | Context |
| Classification | No defect |
| Severity | — |
| Priority | — |
| Models | Gemini Flash-Lite, Claude Sonnet 5.5 Medium, ChatGPT Think, and Perplexity Search, 9 Oct 2026. |
| Prompts | P-002-T1 through P-002-T7 in [prompts.md](../test-data/prompts.md) |

## Summary

The user stores two facts at the start of a normal chat: a preferred language and a reference code. After five unrelated turns the user asks for both back. The chat is short on purpose. A miss would be about this conversation, not about a full context window.

## Preconditions

- One new chat per run.
- Turns sent in order, with no edits and no skipped turns.
- The recall turn asks for only the two facts.

## Steps

1. Open a new chat and send P-002-T1.
2. Send P-002-T2 through P-002-T6, one at a time, waiting for each answer.
3. Send P-002-T7.
4. Compare the reply with Python and `QA-NEEDLE-8841`.
5. Repeat the whole script in two further new chats.

## Expected

The recall reply contains both facts. The language is Python. The code is exactly `QA-NEEDLE-8841`.

## Actual

Gemini Flash-Lite, not signed in, 9 Oct 2026. Three new chats completed all seven turns. Each recall was "Python, QA-NEEDLE-8841". Both facts are exact. No extra sentence. The UI showed no clock.

Claude Sonnet 5.5 Medium, Free plan, 9 Oct 2026. Three new chats completed all seven turns. Run 1 and run 3 recalls: "Python; QA-NEEDLE-8841." Run 2 recall: "Python, and the reference code is QA-NEEDLE-8841." Both facts are exact on all three chats. The extra punctuation and the extra words on run 2 are a format note. The UI showed "just now" rather than a clock time.

ChatGPT Think, Free plan, signed in, 9 Oct 2026. Three new chats completed all seven turns. Run 1 recall was two bullets: "Favorite programming language: Python" and "Reference code: QA-NEEDLE-8841". Runs 2 and 3 were two lines: "Python" and "QA-NEEDLE-8841". Both facts are exact. The labels on run 1 are a format note. The UI showed no clock. No account context appeared in the recalls.

Perplexity Search, 9 Oct 2026. The model name was not shown. Three threads completed all seven turns. Each recall was "Python; QA-NEEDLE-8841." Both facts are exact. The semicolon and the period are a format note. Runs 1 and 2 showed a sources count of 50 beside the answer. Run 3 showed the sources control. The UI showed no clock.

All twelve chats kept both facts. Extra punctuation, labels, or a short connecting phrase, with the code unchanged, is a format note. I did not file it.

## Reproduction

Run 1 through 3 repeat for each environment. Twelve chats in total.

| Run | Environment | Chat | Language | Code | Result |
|---|---|---|---|---|---|
| 1 | Gemini Flash-Lite | `88581a656c811f84` | Python | QA-NEEDLE-8841 | Pass |
| 2 | Gemini Flash-Lite | `5eb9123725ed7243` | Python | QA-NEEDLE-8841 | Pass |
| 3 | Gemini Flash-Lite | `292aa31045ee57f3` | Python | QA-NEEDLE-8841 | Pass |
| 1 | Claude Sonnet 5.5 Medium | `ec25ed23-812a-446f-95cd-8dd0e3a4d603` | Python | QA-NEEDLE-8841 | Pass |
| 2 | Claude Sonnet 5.5 Medium | `756266b3-a934-4e12-b481-ee25f2e85e24` | Python | QA-NEEDLE-8841 | Pass |
| 3 | Claude Sonnet 5.5 Medium | `029bfe93-2228-4a79-bd71-5f30ac57a0a5` | Python | QA-NEEDLE-8841 | Pass |
| 1 | ChatGPT Think | `6ac8dd5e-c64c-83eb-bf94-75cda947e616` | Python | QA-NEEDLE-8841 | Pass |
| 2 | ChatGPT Think | `6ac8dee8-0d54-83ed-b2da-095285d401c1` | Python | QA-NEEDLE-8841 | Pass |
| 3 | ChatGPT Think | `6ac8e05a-4da8-83eb-817a-dbdfbb114507` | Python | QA-NEEDLE-8841 | Pass |
| 1 | Perplexity Search | `cf307683-fd7c-4303-807c-5153314d5c20` | Python | QA-NEEDLE-8841 | Pass |
| 2 | Perplexity Search | `89356128-6565-4c54-9ebd-ea57943598b1` | Python | QA-NEEDLE-8841 | Pass |
| 3 | Perplexity Search | `88ca0052-51b1-4528-9ca2-9d9252fe9b5d` | Python | QA-NEEDLE-8841 | Pass |

## Close

I closed this with no defect. Both facts were exact on every chat. A wrong reference code on at least two runs would have been High, P2, because someone would reuse it. A wrong language with the code still exact would have been Medium, P3.

## Impact

All twelve recalls kept Python and QA-NEEDLE-8841. I would not reuse a wrong code from these chats, because the code did not change.

## Root cause hypothesis

Nothing missed inside these seven turns, so I am not claiming a cause. None of the twelve chats showed that a limit had been reached.

## Workaround

None. No recall failed.

## Evidence

- Gemini run 1 recall: [screenshot](../screenshots/DEF-002-gemini-run1-recall.png), `https://gemini.google.com/app/88581a656c811f84`
- Gemini run 2 recall: [screenshot](../screenshots/DEF-002-gemini-run2-recall.png), `https://gemini.google.com/app/5eb9123725ed7243`
- Gemini run 3 recall: [screenshot](../screenshots/DEF-002-gemini-run3-recall.png), `https://gemini.google.com/app/292aa31045ee57f3`
- Claude run 1 recall: [screenshot](../screenshots/DEF-002-claude-run1-recall.png), `https://claude.ai/chat/ec25ed23-812a-446f-95cd-8dd0e3a4d603`
- Claude run 2 recall: [screenshot](../screenshots/DEF-002-claude-run2-recall.png), `https://claude.ai/chat/756266b3-a934-4e12-b481-ee25f2e85e24`
- Claude run 3 recall: [screenshot](../screenshots/DEF-002-claude-run3-recall.png), `https://claude.ai/chat/029bfe93-2228-4a79-bd71-5f30ac57a0a5`
- ChatGPT run 1 recall: [screenshot](../screenshots/DEF-002-chatgpt-run1-recall.png), `https://chatgpt.com/c/6ac8dd5e-c64c-83eb-bf94-75cda947e616`
- ChatGPT run 2 recall: [screenshot](../screenshots/DEF-002-chatgpt-run2-recall.png), `https://chatgpt.com/c/6ac8dee8-0d54-83ed-b2da-095285d401c1`
- ChatGPT run 3 recall: [screenshot](../screenshots/DEF-002-chatgpt-run3-recall.png), `https://chatgpt.com/c/6ac8e05a-4da8-83eb-817a-dbdfbb114507`
- Perplexity run 1 recall: [screenshot](../screenshots/DEF-002-perplexity-run1-recall.png), `https://www.perplexity.ai/search/cf307683-fd7c-4303-807c-5153314d5c20`
- Perplexity run 2 recall: [screenshot](../screenshots/DEF-002-perplexity-run2-recall.png), `https://www.perplexity.ai/search/89356128-6565-4c54-9ebd-ea57943598b1`
- Perplexity run 3 recall: [screenshot](../screenshots/DEF-002-perplexity-run3-recall.png), `https://www.perplexity.ai/search/88ca0052-51b1-4528-9ca2-9d9252fe9b5d`
