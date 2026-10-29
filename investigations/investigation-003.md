# Investigation 003 — Ambiguous recommendation

| Field | Value |
|---|---|
| Status | Closed, Expected AI Behaviour |
| Ticket | [DEF-004](../defects/DEF-004-Ambiguous-Prompt.md) |
| Question | "Should I use Java?" with no context. Defect, or a normal answer? |

I wrote this up separately because I had to decide whether to file. The answers stayed inside what I had allowed for this prompt.

## What I ran

On each product, 9 Oct 2026:

1. P-004-A in three new chats.
2. I marked what the answer actually did.
3. P-004-B once, with "a new backend service" and a request to state assumptions.

## What I got

| Model | P-004-A | Invented context or a false fact | P-004-B |
|---|---|---|---|
| ChatGPT Think | Three runs. Criteria, then a clarifying question. | All three mentioned a role, experience, a stack, and a project name, with no memory label. I did not file that as an invention. | Assumptions are labeled. The account context from P-004-A is gone. |
| Claude Sonnet 5.5 Medium | Asked what is being built, and gave criteria, on all three. Run 1 also used a memory the UI labeled. | No invented employer, stack, or team. Nothing false about Java as a current fact. | Five assumptions, recommendation still conditional. |
| Gemini Flash-Lite | Asked what is being built, and gave criteria, on all three. | No invented employer, stack, or team. Nothing false about Java as a current fact. | Assumptions under "Core Assumptions", including team proficiency. |
| Perplexity Search | Criteria on all three. Conditional, not a bare yes. | No invented employer, stack, or team. Nothing false about Java as a current fact. | Opens with "I'm assuming you mean". Clearer than P-004-A, same kind of answer. |

## What I closed

I closed DEF-004 as Expected AI Behaviour. I did not get a bare "yes, use Java" with a made-up employer, or a false claim that Java is unsupported.

ChatGPT was the one I checked twice. P-004-A used account context and did not label it. P-004-B labeled assumptions and did not reuse that context. I wrote that down as prompt sensitivity. I did not file it, because I could not see where the context came from. Claude run 1 applied a saved memory and the UI said so. Gemini asked what is being built.

The runs are in [DEF-004](../defects/DEF-004-Ambiguous-Prompt.md).
