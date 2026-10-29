# DEF-005 Inconsistent Behavior

| Field | Value |
|---|---|
| Status | Closed, no defect |
| Category | Consistency |
| Classification | No defect |
| Severity | — |
| Priority | — |
| Models | Perplexity Search, Claude Sonnet 5.5 Medium, ChatGPT Think, and Gemini Flash-Lite, 9 Oct 2026. |
| Prompts | P-005-A in [prompts.md](../test-data/prompts.md) |

## Summary

The same factual prompt is sent in three fresh chats. The fact is stable: the capital of Australia. The case looks for a real contradiction. Different wording is not the defect. A different city is.

## Preconditions

- New chat per run.
- Prompt pasted from P-005-A without edits.
- No memory or custom instructions that would change the answer.

## Steps

1. Send P-005-A in a new chat.
2. Record the city and whether any sentence was added.
3. Repeat in two further new chats.
4. Compare the three cities. Do not merge chats.

## Expected

Every run names Canberra. Extra words do not fail the check when the city is correct.

## Actual

Perplexity Search, 9 Oct 2026. The model name was not shown. Three new chats each returned Canberra. A Britannica source badge sits beside the city. Follow-up suggestion chips under the answer are UI, not part of the answer. The three cities agree, so there is no inconsistency on this product.

Claude Sonnet 5.5 Medium, Free plan, 9 Oct 2026. Three new chats each returned only Canberra. No extra sentence.

ChatGPT Think, Free plan, 9 Oct 2026. The answer UI showed no clock. Three new chats each returned only Canberra. On run 3 a usage banner sat under the answer ("Files, images, and data analysis are unavailable until usage resets at 3:53 PM"). I did not count that banner as part of the answer.

Gemini Flash-Lite, not signed in, 9 Oct 2026. The answer UI showed no clock. Three new chats each returned only Canberra. No extra sentence.

## Reproduction

Each row is a new chat. I did not count Regenerate as a run.

### Perplexity, Search

| Run | Environment | Time | City | Extra text in the answer | Result |
|---|---|---|---|---|---|
| 1 | Perplexity Search | 12:23 | Canberra | Source badge only | Pass |
| 2 | Perplexity Search | 12:26 | Canberra | Source badge only | Pass |
| 3 | Perplexity Search | 12:28 | Canberra | Source badge only | Pass |

### Claude, Sonnet 5.5 Medium

| Run | Chat | Time | City | Extra text | Result |
|---|---|---|---|---|---|
| 1 | `b3bc35a0-2c51-4352-af9f-1d4d6973b7c2` | 12:42 | Canberra | None | Pass |
| 2 | `469304a9-44f0-45c7-84f4-2d602491aced` | 12:43 | Canberra | None | Pass |
| 3 | `7edc68ee-d89c-43b1-9717-9ea2dfedaaa4` | 12:44 | Canberra | None | Pass |

### ChatGPT, Think

The UI showed no clock on these answers.

| Run | Chat | City | Extra text in the answer | Result |
|---|---|---|---|---|
| 1 | `6ac8bfcc-b28c-83eb-8b7b-eb66b824079f` | Canberra | None | Pass |
| 2 | `6ac8c0b4-979c-83ed-ad9c-ccf0e62de5dc` | Canberra | None | Pass |
| 3 | `6ac8c184-d720-83eb-9786-9f321fc499d0` | Canberra | None. A usage banner sat under the answer. | Pass |

### Gemini, Flash-Lite

Not signed in. The UI showed no clock.

| Run | Chat | City | Extra text | Result |
|---|---|---|---|---|
| 1 | `261e8f56d05c8fa8` | Canberra | None | Pass |
| 2 | `9dd3357e049b9e6f` | Canberra | None | Pass |
| 3 | `f67bd1d046715061` | Canberra | None | Pass |

## Close

I closed this with no defect. All three runs on each product said Canberra. One wrong city next to a correct one would have been the inconsistency, High, P2. Three identical wrong cities would have been a factual defect, and I would have said so. I did not see either.

## Impact

All twelve chats named Canberra. I would not have copied a wrong capital from these runs.

## Root cause hypothesis

None. On each product, three fresh chats on 9 Oct 2026 agreed. That does not tell me anything about sampling or settings.

## Workaround

None. Asking the model to stay consistent with an earlier chat would have been a different prompt. I did not send that.

## Evidence

- Perplexity run 1, 12:23: [screenshot](../screenshots/DEF-005-perplexity-P005A-run1.png), `https://www.perplexity.ai/search/149ee0bb-5fa5-4634-a338-bfae397af3fb`
- Perplexity run 2, 12:26: [screenshot](../screenshots/DEF-005-perplexity-P005A-run2.png), `https://www.perplexity.ai/search/fbb5d4ba-a6b2-44e0-80de-76de79c3240f`
- Perplexity run 3, 12:28: [screenshot](../screenshots/DEF-005-perplexity-P005A-run3.png), `https://www.perplexity.ai/search/dec2fcb6-4e65-440f-b785-a43af36733c9`
- Claude run 1, 12:42: [screenshot](../screenshots/DEF-005-claude-P005A-run1.png), `https://claude.ai/chat/b3bc35a0-2c51-4352-af9f-1d4d6973b7c2`
- Claude run 2, 12:43: [screenshot](../screenshots/DEF-005-claude-P005A-run2.png), `https://claude.ai/chat/469304a9-44f0-45c7-84f4-2d602491aced`
- Claude run 3, 12:44: [screenshot](../screenshots/DEF-005-claude-P005A-run3.png), `https://claude.ai/chat/7edc68ee-d89c-43b1-9717-9ea2dfedaaa4`
- ChatGPT run 1: [screenshot](../screenshots/DEF-005-chatgpt-P005A-run1.png), `https://chatgpt.com/c/6ac8bfcc-b28c-83eb-8b7b-eb66b824079f`
- ChatGPT run 2: [screenshot](../screenshots/DEF-005-chatgpt-P005A-run2.png), `https://chatgpt.com/c/6ac8c0b4-979c-83ed-ad9c-ccf0e62de5dc`
- ChatGPT run 3: [screenshot](../screenshots/DEF-005-chatgpt-P005A-run3.png), `https://chatgpt.com/c/6ac8c184-d720-83eb-9786-9f321fc499d0`
- Gemini run 1: [screenshot](../screenshots/DEF-005-gemini-P005A-run1.png), `https://gemini.google.com/app/261e8f56d05c8fa8`
- Gemini run 2: [screenshot](../screenshots/DEF-005-gemini-P005A-run2.png), `https://gemini.google.com/app/9dd3357e049b9e6f`
- Gemini run 3: [screenshot](../screenshots/DEF-005-gemini-P005A-run3.png), `https://gemini.google.com/app/f67bd1d046715061`

## Notes

Twelve new chats named Canberra. A source badge next to the right city is not an inconsistency. The ChatGPT usage banner is not part of the answer.
