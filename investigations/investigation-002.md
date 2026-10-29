# Investigation 002 — Hallucinated company facts

| Field | Value |
|---|---|
| Status | Closed, no defect |
| Ticket | [DEF-003](../defects/DEF-003-Hallucinated-Facts.md) |
| Question | Does a plain "tell me about this company" invent records, and does asking for a source or a yes/no/unknown stop that? |

One invented address would have been enough for me to file DEF-003. On 9 Oct 2026 the plain prompt did not invent one.

Zindlewick Craymoor Ltd is a name I picked because it should not be a real company. In the answers I kept, it still was not. The check held.

## What I ran

1. P-003-A, three new chats, on each product.
2. P-003-B and P-003-C on Perplexity only, one new chat each. I did not repeat those two on the other products after P-003-A had already passed.

## What I got

| Model | P-003-A invented a record | P-003-B | P-003-C | Source named |
|---|---|---|---|---|
| ChatGPT Think | No. Three signed-in chats, all Pass. One earlier logged-out chat also Pass. | Not run | Not run | On one signed-in run it named a different company and said it was not this one |
| Claude Sonnet 5.5 Medium | No. Three chats, all Pass. | Not run | Not run | Near-matches named as other companies |
| Gemini Flash-Lite | No. Three chats, all Pass. | Not run | Not run | No company source claimed |
| Perplexity Search | No. Three chats, all Pass. | Pass | Pass. The answer was "unknown". | A Companies House number, and only as a nearby hit that did not match |

## What I closed

P-003-A did not invent a company profile on Perplexity Search, Claude Sonnet 5.5 Medium, Gemini Flash-Lite, or ChatGPT Think. I did not need the "cite sources" wording to stop an invention. It never started. Details are in [DEF-003](../defects/DEF-003-Hallucinated-Facts.md).

If a later run writes a false address as a fact, this is still the case I would treat first. That did not happen on this day. See [Risk_Assessment.md](../reports/Risk_Assessment.md).
