# Risk assessment

9 Oct 2026. I only mark a risk as confirmed when the ticket has a Fail. These passes are not confirmed risks.

I used the severity rules in [defect-rules.md](../standards/defect-rules.md). I cared about what a user might do with the answer, not about a rate from three chats.

- Critical, for me, means someone could pay, sign, partner, or take a compliance action on a false fact.
- High means they could paste or forward something that looks like a record or a settled fact.
- Medium means they asked for a shape, such as exactly three items, and got a different shape, while the content itself is not a false record.

## What I was watching for

| ID | What a user might do | What would go wrong | Severity if I had a Fail | What happened |
|---|---|---|---|---|
| [DEF-001](../defects/DEF-001-Instruction-Following.md) | Paste the list into a test document | The document has items they did not ask for | Medium | Did not happen on Perplexity Search, ChatGPT Think, Claude Sonnet 5.5 Medium, or Gemini Flash-Lite. |
| [DEF-002](../defects/DEF-002-Context-Loss.md) | Reuse the reference code later in the same chat | The wrong code lands in notes or a sample | High if the code is wrong. Medium if only the language is wrong | Did not happen on Gemini Flash-Lite, Claude Sonnet 5.5 Medium, ChatGPT Think, or Perplexity Search. |
| [DEF-003](../defects/DEF-003-Hallucinated-Facts.md) | Forward a company profile | Someone treats a made-up address, number, or director as research | High. Critical only if the answer also pushes an action on that profile | Did not happen on Perplexity Search, Claude Sonnet 5.5 Medium, Gemini Flash-Lite, or ChatGPT Think. |
| [DEF-004](../defects/DEF-004-Ambiguous-Prompt.md) | Treat the Java answer as a decision | Low when the assumption is visible. High if the answer invents their stack or a current fact about Java | Same split. Critical only if it also tells them to act on the false fact | I did not see an invented fact on Perplexity Search, Claude Sonnet 5.5 Medium, ChatGPT Think, or Gemini Flash-Lite. |
| [DEF-005](../defects/DEF-005-Inconsistent-Behavior.md) | Copy the capital from a fresh chat | A wrong city goes into a document, and another chat would have said something else | High if the city changes | Did not happen. All twelve chats said Canberra. |

## Where I landed

All five are closed. No false company record. No invented user fact on the Java question. ChatGPT did use unlabeled account context on P-004-A, and labeled assumptions on P-004-B. I did not file that as an invented fact. The city did not change. The list stayed at three items. The recall kept Python and QA-NEEDLE-8841 on all twelve chats.

I am not going to quote three runs as the chance that a user gets hurt. I also will not list a workaround as mitigation unless I have a Pass on that workaround in its own chat.
