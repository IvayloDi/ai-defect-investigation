# Defect rules

These are the rules I used before I closed a ticket. If an answer felt wrong but did not break one of these, I did not file it.

I wrote each ticket so someone who cannot open the chat can still see the prompt, the output, and what I expected.

## Classification

One main label. A second label only when it describes the condition, not a second defect.

### Product Defect

The assistant broke something the user actually asked for, or it stated a made-up specific as a fact.

Examples I would file:

- I asked for exactly three items and the answer added a fourth advantage.
- I asked about a company and the answer gave an address, registration number, director, or revenue with no source in that answer.

### Known Limitation

The product already says this is a limit, or the behaviour only showed up after that limit was hit. A short chat that drops a reference code is not "context window" unless the UI showed that a limit had been reached.

### Expected AI Behaviour

The prompt can be answered in more than one acceptable way. The assistant asks what I am deciding, or it states an assumption and gives criteria. Different wording with the same facts is fine.

### Prompt Sensitivity

The answer changes when I change the prompt a little, in a way that matters. I use this as the main label when that change is what the ticket is about. A short "give 3 bullets" can pass while "give exactly 3 bullets and explain each" fails. I also call it a product defect when the stricter prompt is still a fair request and the product breaks it.

## Severity

Severity is the harm if someone trusts the answer. It is not how odd the answer looked.

| Severity | When I use it |
|---|---|
| Critical | A false fact is stated as settled, and someone could pay, sign, partner, or take a legal, medical, or safety action on it. |
| High | The answer is wrong or unsupported, and someone is likely to copy it or forward it. |
| Medium | A constraint I set was missed: count, language, or shape. The content may still be usable. |
| Low | The wording or layout is off. The facts and the constraints still hold. |

An extra advantage in a list is Medium, not Critical. A made-up company address written as a record is High. It is Critical only if the answer also tells the user to pay, sign, or partner on that record.

## Priority

This is what I would tell a product owner. It is my recommendation. It does not fix the product.

| Priority | What I mean |
|---|---|
| P1 | Look at this before people rely on the answer for a decision that has consequences. |
| P2 | Schedule it soon. People are likely to repeat or forward the wrong content. |
| P3 | Schedule it. The user can still see the output and edit it. |
| P4 | Backlog. Formatting or wording only. |

## How I reproduced

- New chat for every run. Regenerate is not one of the three. I can note a regenerate separately.
- Same prompt text on the three runs. A different prompt is a different check.
- Public web UI. I did not change account settings.
- I wrote down the model label from the UI, the URL, and the date.
- Pass or Fail against the check in the ticket, plus one sentence of what was on screen.
- Three runs stay as Pass and Fail. I do not write a percentage.

I do not call something a workaround until I have run that text in a new chat and it passed. If I never claimed a workaround, the ticket says none.

## Root cause

I only write a hypothesis after I have run the boundary prompt. I name what separated pass from fail. I do not upgrade that to a proven cause.
