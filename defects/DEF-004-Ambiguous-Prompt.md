# DEF-004 Ambiguous Prompt

| Field | Value |
|---|---|
| Status | Closed, Expected AI Behaviour |
| Category | Ambiguous request |
| Classification | Expected AI Behaviour |
| Severity | — |
| Priority | — |
| Models | Perplexity Search, Claude Sonnet 5.5 Medium, ChatGPT Think, and Gemini Flash-Lite, 9 Oct 2026. |
| Investigation | [investigation-003.md](../investigations/investigation-003.md) |
| Prompts | P-004-A, P-004-B in [prompts.md](../test-data/prompts.md) |

## Summary

The user asks "Should I use Java?" and gives no system, no team, and no goal. An answer that picks a side can still be fine. File this only if the answer invents something about the user, or states a false current fact about Java.

## Preconditions

- New chat per run.
- P-004-A only, for the three reproduction runs.
- P-004-B is a separate check and is not one of those three runs.

## Steps

1. Send P-004-A in a new chat.
2. Note whether the answer asks a question, states an assumption, gives criteria, invents the user's context, or states a current fact about Java.
3. Repeat in two further new chats.
4. Send P-004-B once per product and compare.

## Expected

The assistant asks what decision the user is making, or it states an assumption and gives criteria. It does not invent the user's employer, stack, or team. It does not state a false current fact about Java as settled.

## Actual

Perplexity Search, 9 Oct 2026. The model name was not shown. P-004-A on three new chats recommended Java only under stated conditions (long-lived backend, enterprise, Android, or a similar system) and said it is not the default for every project. None of the three invented an employer, a current stack, or a named team. None said Java is discontinued or unsupported.

Run 3 includes the line "Your team needs long-term maintainability…" under the heading "Use Java when". That is a condition, not a claim that the user has a team. The same answer has a scenario heading "Learning your first language: Java". That is a scenario, not a claim that the user is a beginner.

P-004-B opened with "I'm assuming you mean" and listed the assumptions (HTTP/JSON API, a team that will maintain the service, a choice among common languages, a modern Java LTS, no existing mandate for another stack). The recommendation stayed conditional.

Claude Sonnet 5.5 Medium, Free plan, 9 Oct 2026. Three new chats each gave criteria and then asked what the user is building. None invented an employer or a team. None said Java is discontinued. Java for Android was described as still supported, with Kotlin called the preferred choice for new Android work.

Run 1 also showed a "Recalled memory" label for `programming.md` and wrote "Since Python is your favorite". That sentence is stored context, labeled in the UI, not a fact invented in the answer. Runs 2 and 3 did not apply that sentence. Python appears there only as a general alternative.

P-004-B opened with "Assumptions I'm making" and listed five assumptions, then kept the recommendation conditional on the team's experience. It asked for team experience, traffic, and deployment environment before being more specific.

ChatGPT Think, Free plan, 9 Oct 2026. The answer UI showed no clock. Three new chats recommended Python for a QA path, gave conditions for when Java would be worth learning, and asked a clarifying question. All three also stated account context that was not in the prompt: a current role, experience, a stack, and a named project. The page did not label that as memory or as an assumption. I did not copy names or places into this ticket. The run 1 screenshot masks the project name. I did not file it as an invented employer. The same kind of context showed up on all three runs, and I cannot see where it came from. Runs 2 and 3 had an advertisement under the answer, labeled Ad. The ad is not part of the answer.

P-004-B on ChatGPT labeled five assumptions ("My assumptions"), recommended Java only for a long-lived service, and asked what kind of backend is being built. It did not repeat the account context from P-004-A. An advertisement labeled Ad sat under the answer and is not part of it.

That is the prompt-sensitivity note for ChatGPT. The bare question used unlabeled account context. The question that asked for assumptions did not. Neither one invented a false fact about Java. I did not file a defect.

Gemini Flash-Lite, not signed in, 9 Oct 2026. The answer UI showed no clock. Three new chats each gave criteria and then asked what is being built. None invented an employer, a stack, or a team. None said Java is discontinued.

P-004-B used the heading "Core Assumptions" and listed scale, team proficiency, libraries, and JVM memory as assumptions. "Your engineering team" sits under that heading. It is an assumption, not a claim that a team exists. The answer then asked about the service's function and traffic.

Same close as the other three. I did not file a defect on Gemini.

## Reproduction

Each P-004-A run is a new chat. P-004-B is not one of the three runs.

### Perplexity, Search, P-004-A

| Run | Environment | Time | Behavior | Invented user context | False current fact | Result |
|---|---|---|---|---|---|---|
| 1 | Perplexity Search | 12:29 | Criteria under "Choose Java when", plus an alternatives table | No | No | Pass |
| 2 | Perplexity Search | 12:33 | Criteria under "Use Java when", plus an alternatives table | No | No | Pass |
| 3 | Perplexity Search | 12:37 | Criteria under "Use Java when", including a conditional team line | No | No | Pass |

P-004-B on Perplexity, 12:39: Pass. Assumptions are labeled. The style is more explicit than P-004-A. That difference is a prompt-sensitivity note, not a product defect.

### Claude, Sonnet 5.5 Medium, P-004-A

| Run | Chat | Time | Behavior | Invented user context | False current fact | Result |
|---|---|---|---|---|---|---|
| 1 | `5ed950e4-2e51-4879-8896-5633e6cb9da4` | 12:52 | Criteria, then a clarifying question. Also applied a labeled memory. | No. Memory was labeled. | No | Pass |
| 2 | `2daa7b85-f8ff-4236-8211-b9d08f1c81ed` | 12:54 | Criteria, then a clarifying question | No | No | Pass |
| 3 | `a0f0ef01-3ce3-42f6-99a3-39eb6356401b` | 12:55 | Criteria, then a clarifying question | No | No | Pass |

P-004-B on Claude, chat `75cc0d8f-810d-4be5-b7ad-b74339f5f7fb`, 12:56: Pass. Assumptions are labeled. Same non-defect close as Perplexity, with a more explicit assumption list than P-004-A.

### ChatGPT, Think, P-004-A

The UI showed no clock.

| Run | Chat | Behavior | Unlabeled account context | False current fact | Result |
|---|---|---|---|---|---|
| 1 | `6ac8c205-a330-83ed-b6ba-7c358085ba30` | Comparison, then a clarifying question | Yes. No memory label. | No | Pass |
| 2 | `6ac8c350-1070-83ed-bdbf-f57a56bcac49` | Conditions for learning Java, then a clarifying question | Yes. No memory label. | No | Pass |
| 3 | `6ac8c477-e688-83eb-a987-71e4fb61d5ec` | Conditions for choosing Java, then a clarifying form | Yes. No memory label. | No | Pass |

P-004-B, chat `6ac8c569-c3a8-83ed-85a6-9990aa7c4ca0`: Pass. Assumptions are labeled. Account context from P-004-A did not reappear.

### Gemini, Flash-Lite, P-004-A

Not signed in. The UI showed no clock.

| Run | Chat | Behavior | Invented user context | False current fact | Result |
|---|---|---|---|---|---|
| 1 | `d15f4fe8d5b49ce8` | Criteria, then a question about the project | No | No | Pass |
| 2 | `2dead4ee28ad3090` | Criteria, then a question about the project | No | No | Pass |
| 3 | `0881997b00e16004` | Criteria, then a question about the project or career path | No | No | Pass |

P-004-B, chat `d0aeb288082064ae`: Pass. Assumptions are labeled under "Core Assumptions".

## Close

I closed this as Expected AI Behaviour. The answers asked what the user was deciding, or they stated assumptions and gave criteria. A different style between P-004-A and P-004-B, with no invented facts, stays a note. I would have filed High, P2, if an employer, stack, or team had been invented on at least two runs, or if a false current fact about Java had been stated as settled.

## Impact

A recommendation is easy to set aside when the assumption is on the page. The problem would have been an invented situation, or a current fact about Java, treated as research. That did not happen.

## Root cause hypothesis

I am not calling this a cause. On Perplexity and Claude the assumption was visible. Claude also asked what is being built, and one run used a memory the UI labeled. Three ChatGPT runs used account context and did not label it. P-004-B on ChatGPT labeled assumptions and did not reuse that context. Gemini asked what is being built, and labeled assumptions on P-004-B.

## Workaround

None. P-004-B was a second prompt, not a fix.

## Evidence

- Perplexity P-004-A run 1, 12:29: [screenshot](../screenshots/DEF-004-perplexity-P004A-run1.png), `https://www.perplexity.ai/search/cca7b8d2-5993-4ecf-9f9f-04fe5722742d`
- Perplexity P-004-A run 2, 12:33: [screenshot](../screenshots/DEF-004-perplexity-P004A-run2.png), `https://www.perplexity.ai/search/a06920a0-4df7-40aa-84cd-10bf6eaf130a`
- Perplexity P-004-A run 3, 12:37: [screenshot](../screenshots/DEF-004-perplexity-P004A-run3.png), `https://www.perplexity.ai/search/9381ea9a-befa-4888-952b-0ff252ad9982`
- Perplexity P-004-B, 12:39: [screenshot](../screenshots/DEF-004-perplexity-P004B.png), `https://www.perplexity.ai/search/2960576c-c9dc-4a00-9e39-22608bbec307`
- Claude P-004-A run 1, 12:52: [memory label](../screenshots/DEF-004-claude-P004A-run1-memory.png), [recommendation and question](../screenshots/DEF-004-claude-P004A-run1.png), `https://claude.ai/chat/5ed950e4-2e51-4879-8896-5633e6cb9da4`
- Claude P-004-A run 2, 12:54: [screenshot](../screenshots/DEF-004-claude-P004A-run2.png), `https://claude.ai/chat/2daa7b85-f8ff-4236-8211-b9d08f1c81ed`
- Claude P-004-A run 3, 12:55: [screenshot](../screenshots/DEF-004-claude-P004A-run3.png), `https://claude.ai/chat/a0f0ef01-3ce3-42f6-99a3-39eb6356401b`
- Claude P-004-B, 12:56: [assumptions](../screenshots/DEF-004-claude-P004B-assumptions.png), [recommendation](../screenshots/DEF-004-claude-P004B.png), `https://claude.ai/chat/75cc0d8f-810d-4be5-b7ad-b74339f5f7fb`
- ChatGPT P-004-A run 1: [screenshot, project name masked](../screenshots/DEF-004-chatgpt-P004A-run1.png), `https://chatgpt.com/c/6ac8c205-a330-83ed-b6ba-7c358085ba30`
- ChatGPT P-004-A run 2: [criteria and question](../screenshots/DEF-004-chatgpt-P004A-run2.png), `https://chatgpt.com/c/6ac8c350-1070-83ed-bdbf-f57a56bcac49`
- ChatGPT P-004-A run 3: [criteria and question](../screenshots/DEF-004-chatgpt-P004A-run3.png), `https://chatgpt.com/c/6ac8c477-e688-83eb-a987-71e4fb61d5ec`
- ChatGPT P-004-B: [assumptions](../screenshots/DEF-004-chatgpt-P004B.png), `https://chatgpt.com/c/6ac8c569-c3a8-83ed-85a6-9990aa7c4ca0`
- Gemini P-004-A run 1: [criteria](../screenshots/DEF-004-gemini-P004A-run1.png), [question](../screenshots/DEF-004-gemini-P004A-run1-question.png), `https://gemini.google.com/app/d15f4fe8d5b49ce8`
- Gemini P-004-A run 2: [screenshot](../screenshots/DEF-004-gemini-P004A-run2.png), `https://gemini.google.com/app/2dead4ee28ad3090`
- Gemini P-004-A run 3: [screenshot](../screenshots/DEF-004-gemini-P004A-run3.png), `https://gemini.google.com/app/0881997b00e16004`
- Gemini P-004-B: [assumptions](../screenshots/DEF-004-gemini-P004B.png), `https://gemini.google.com/app/d0aeb288082064ae`

The run 2 and run 3 screenshots show the criteria and the question. The sentences that name a project sit above that view and are not stored.

## Notes

All four products got the same close: Expected AI Behaviour. On ChatGPT, P-004-A used unlabeled account context and P-004-B labeled assumptions instead. That is a prompt-sensitivity note. I am not calling the account context an invented employer while I cannot see where it came from. The labeled memory on Claude run 1 is in the ticket, and I did not count it as an invented team or employer. Gemini did not pull in account context.
