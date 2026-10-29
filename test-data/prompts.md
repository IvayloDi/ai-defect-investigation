# Prompts

This is the only copy of the text I sent. The tickets point here so I don't end up with two wordings.

What I kept the same on every run:

- New chat.
- Public web UI of ChatGPT, Claude, Gemini, or Perplexity.
- I did not change settings, memory, or custom instructions between runs.
- I wrote down the model label that was actually on screen.

## DEF-001 Instruction following

### P-001-A Base

```text
List exactly 3 advantages of API testing.
```

Pass: exactly three advantages. A fourth advantage is a fail. A title line that does not add another advantage is not a fail.

### P-001-B Short count

```text
Give 3 bullets about advantages of API testing.
```

Pass: three bullets. I was going to use this as the looser wording. I did not treat a preamble as strictly as on P-001-A.

Not executed on 9 Oct 2026.

### P-001-C Count plus explanation

```text
Give exactly 3 bullets about advantages of API testing and explain each in one sentence.
```

Pass: exactly three bullets, each with one explanation, and no fourth advantage.

### P-001-W Workaround candidate

```text
Return ONLY 3 advantages of API testing, as a numbered list from 1 to 3. Do not add a fourth.
```

Pass: items 1, 2, and 3 only.

Not executed on 9 Oct 2026. P-001-A passed, so I did not use this as a workaround.

## DEF-002 Context

Send the turns in order inside one chat. That whole chat is one run. Repeat the script in two further new chats.

### P-002-T1

```text
Remember two facts for this chat only. My favorite programming language is Python. The reference code is QA-NEEDLE-8841.
```

### P-002-T2

```text
In one sentence, what is regression testing?
```

### P-002-T3

```text
Name one reason a tester would prefer an API check over a UI check.
```

### P-002-T4

```text
What does HTTP 404 mean? One sentence.
```

### P-002-T5

```text
Give one example of a boundary value for a field that accepts 1 to 10.
```

### P-002-T6

```text
What is a defect severity used for? One sentence.
```

### P-002-T7 Recall

```text
What programming language did I say I prefer, and what reference code did I give you? Reply with only those two facts.
```

Pass: the language is Python and the code is exactly `QA-NEEDLE-8841`. Missing either fact is a fail. Extra prose is a format note when both facts are present and exact. I did not fail the recall for that, and I did not open a separate defect for it.

I kept it to seven turns on purpose. The chat stays a normal conversation, so if a fact had gone missing I could not blame a full context window unless the product showed that a limit had been reached.

## DEF-003 Hallucinated facts

### P-003-A Confident

```text
Tell me about Zindlewick Craymoor Ltd.
```

### P-003-B Sources

```text
Tell me about Zindlewick Craymoor Ltd. Cite primary sources and quote them. If you cannot find the company, say so.
```

### P-003-C Existence

```text
Does Zindlewick Craymoor Ltd exist? Answer yes, no, or unknown. Do not add company details unless you have a source you can name.
```

Pass on all three: the answer says the company cannot be verified, is unknown, or was not found, and it adds no address, registration number, director, founding year, or revenue. Fail when any of those is stated as fact with no source in the answer.

Zindlewick Craymoor Ltd is a name I picked because it should not be a real company. If a run had shown that it is, I would have stopped and written that the check failed. I would not have filed a hallucination from that run.

## DEF-004 Ambiguous prompt

### P-004-A Underspecified

```text
Should I use Java?
```

Pass, and classify it as Expected AI Behaviour, when the answer asks what decision the user is making or states an assumption and gives criteria. Fail it as a product defect only when it invents the user's employer, current stack, or team, or states a false current fact about Java as settled (for example, that Java is no longer supported).

### P-004-B Slightly specified

```text
Should I use Java for a new backend service? State your assumptions.
```

I used this to see whether the answer changes once I add a bit of context. It is a sensitivity check, not a second defect by default.

## DEF-005 Inconsistent behavior

### P-005-A Stable fact

```text
What is the capital of Australia? Answer with the city name only.
```

Pass: the city is Canberra. Three new chats that all say Canberra pass, even if I learn nothing else from them. Any other city is a fail. Extra sentences with the right city are a format note, not an inconsistency.

I used a stable fact so a contradiction would mean something. An opinion would vary for reasons this ticket is not about.
