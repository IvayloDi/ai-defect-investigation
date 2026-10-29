# DEF-001 Instruction Following

| Field | Value |
|---|---|
| Status | Closed, no defect |
| Category | Instruction Following |
| Classification | No defect |
| Severity | — |
| Priority | — |
| Models | Perplexity Search, ChatGPT Think, Claude Sonnet 5.5 Medium, and Gemini Flash-Lite, 9 Oct 2026. |
| Investigation | [investigation-001.md](../investigations/investigation-001.md) |
| Prompts | P-001-A and P-001-C in [prompts.md](../test-data/prompts.md). P-001-B and P-001-W were not run. |

## Summary

The user asks for exactly three advantages of API testing. The check is the count. A fuller answer still fails if a fourth advantage is in it.

## Preconditions

- New chat on the public web UI.
- No custom instructions and no uploaded files.
- Prompt text pasted from P-001-A without edits.

## Steps

1. Open a new chat.
2. Send P-001-A.
3. Count advantages. A title that does not add an advantage does not increase the count.
4. Repeat in two further new chats.
5. Send P-001-C in one new chat.

## Expected

Exactly three advantages. No fourth advantage.

## Actual

Perplexity Search, 9 Oct 2026. The model name was not shown. P-001-A came back with exactly three advantages on three new chats. P-001-C came back with exactly three bullets, each with one sentence. No fourth advantage. I did not count the follow-up chips under the answer.

ChatGPT, mode Think, Free plan, 9 Oct 2026. P-001-A returned exactly three advantages on three new chats. P-001-C returned exactly three bullets, one sentence each.

Claude Sonnet 5.5 Medium, Free plan, 9 Oct 2026. P-001-A returned exactly three advantages on three new chats. P-001-C returned exactly three bullets. No fourth advantage appeared.

Gemini Flash-Lite, not signed in, 9 Oct 2026. The answer UI showed no clock. P-001-A returned exactly three advantages on three new chats. A title line was not counted as an advantage. P-001-C returned exactly three bullets, one sentence each. No fourth advantage appeared.

## Reproduction

Each row is a new chat. I did not count Regenerate as a run.

### Perplexity, Search, P-001-A

| Run | Environment | Time | Result | Observation |
|---|---|---|---|---|
| 1 | Perplexity Search | 9:56 | Pass | Three advantages: faster feedback, earlier defect detection, security and coverage. |
| 2 | Perplexity Search | 9:57 | Pass | Three advantages: faster feedback, broader coverage, lower costs. |
| 3 | Perplexity Search | 9:57 | Pass | Three advantages: faster feedback, earlier defect detection, broader coverage. |

P-001-C on Perplexity, one new chat at 9:58: Pass. Three bullets, one sentence each.

### ChatGPT, Think, P-001-A

| Run | Chat | Result | Observation |
|---|---|---|---|
| 1 | `6ac89e6c-eddc-83ed-a44c-b1b71b23bb49` | Pass | Three numbered advantages. |
| 2 | `6ac89ea2-fbfc-83ed-b706-28e652cdb7cc` | Pass | Three numbered advantages. |
| 3 | `6ac89ed9-db8c-83eb-9c26-761475c07daf` | Pass | Three numbered advantages. |

P-001-C on ChatGPT, chat `6ac89f19-c984-83ed-a5c5-ed9005d6b55f`: Pass. Three bullets, one sentence each.

### Claude, Sonnet 5.5 Medium, P-001-A

| Run | Chat | Time | Result | Observation |
|---|---|---|---|---|
| 1 | `5c3fc75d-883d-49b5-9f12-75798980cb7c` | 12:59 | Pass | Three numbered advantages. |
| 2 | `d2422338-6c11-4371-abb4-42273eebed51` | 13:01 | Pass | Three numbered advantages. A title line is not a fourth item. |
| 3 | `27c5e801-190a-499f-a3cf-f0493b412ee1` | 13:03 | Pass | Three numbered advantages. A title line is not a fourth item. |

P-001-C on Claude, chat `0f1e8f71-108d-44f1-a6f0-0171beb50475`, 13:07: Pass. Three bullets.

### Gemini, Flash-Lite, P-001-A

Not signed in. The UI showed no clock.

| Run | Chat | Result | Observation |
|---|---|---|---|
| 1 | `458d73a7bedb2154` | Pass | Three advantages. A title line is not a fourth item. |
| 2 | `ff56a8c7aec693a4` | Pass | Three advantages. |
| 3 | `5f0552d528266e13` | Pass | Three advantages. A title line is not a fourth item. |

P-001-C on Gemini, chat `694aca8354dd47d5`: Pass. Three bullets, one sentence each.

## Close

I closed this with no defect. The count held on every run. If a fourth real advantage had shown up on at least two runs of P-001-A, I would have filed a product defect, Medium, P3. A false statement in that extra item would have been a different ticket.

## Impact

No fourth advantage. The lists were the length I asked for.

## Root cause hypothesis

I don't have one. On all four products, adding "explain each in one sentence" still returned three items.

## Workaround

None. P-001-A passed, so I never sent P-001-W.

## Evidence

- Perplexity P-001-A run 1: [screenshot](../screenshots/DEF-001-perplexity-P001A-run1.png), `https://www.perplexity.ai/search/2ccf7e75-8719-4766-9bc1-58ee47038ef8`
- Perplexity P-001-A run 2: [screenshot](../screenshots/DEF-001-perplexity-P001A-run2.png), `https://www.perplexity.ai/search/7e320401-31bb-4d6c-8454-c1128deb51a1`
- Perplexity P-001-A run 3: [screenshot](../screenshots/DEF-001-perplexity-P001A-run3.png), `https://www.perplexity.ai/search/a5eca5b0-559f-4134-ac15-3f0d1fe86235`
- Perplexity P-001-C: [screenshot](../screenshots/DEF-001-perplexity-P001C.png), `https://www.perplexity.ai/search/a84d4591-3e6c-478d-b0da-a633e2529109`
- ChatGPT P-001-A run 1: [screenshot](../screenshots/DEF-001-chatgpt-P001A-run1.png), `https://chatgpt.com/c/6ac89e6c-eddc-83ed-a44c-b1b71b23bb49`
- ChatGPT P-001-A run 2: [screenshot](../screenshots/DEF-001-chatgpt-P001A-run2.png), `https://chatgpt.com/c/6ac89ea2-fbfc-83ed-b706-28e652cdb7cc`
- ChatGPT P-001-A run 3: [screenshot](../screenshots/DEF-001-chatgpt-P001A-run3.png), `https://chatgpt.com/c/6ac89ed9-db8c-83eb-9c26-761475c07daf`
- ChatGPT P-001-C: [screenshot](../screenshots/DEF-001-chatgpt-P001C.png), `https://chatgpt.com/c/6ac89f19-c984-83ed-a5c5-ed9005d6b55f`
- Claude P-001-A run 1, 12:59: [screenshot](../screenshots/DEF-001-claude-P001A-run1.png), `https://claude.ai/chat/5c3fc75d-883d-49b5-9f12-75798980cb7c`
- Claude P-001-A run 2, 13:01: [screenshot](../screenshots/DEF-001-claude-P001A-run2.png), `https://claude.ai/chat/d2422338-6c11-4371-abb4-42273eebed51`
- Claude P-001-A run 3, 13:03: [screenshot](../screenshots/DEF-001-claude-P001A-run3.png), `https://claude.ai/chat/27c5e801-190a-499f-a3cf-f0493b412ee1`
- Claude P-001-C, 13:07: [screenshot](../screenshots/DEF-001-claude-P001C.png), `https://claude.ai/chat/0f1e8f71-108d-44f1-a6f0-0171beb50475`
- Gemini P-001-A run 1: [screenshot](../screenshots/DEF-001-gemini-P001A-run1.png), `https://gemini.google.com/app/458d73a7bedb2154`
- Gemini P-001-A run 2: [screenshot](../screenshots/DEF-001-gemini-P001A-run2.png), `https://gemini.google.com/app/ff56a8c7aec693a4`
- Gemini P-001-A run 3: [screenshot](../screenshots/DEF-001-gemini-P001A-run3.png), `https://gemini.google.com/app/5f0552d528266e13`
- Gemini P-001-C: [screenshot](../screenshots/DEF-001-gemini-P001C.png), `https://gemini.google.com/app/694aca8354dd47d5`
