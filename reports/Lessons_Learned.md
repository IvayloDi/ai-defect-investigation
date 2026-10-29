# Lessons learned

9 Oct 2026. The rules I used are in [defect-rules.md](../standards/defect-rules.md). This note is only what surprised me.

- On [DEF-001](../defects/DEF-001-Instruction-Following.md) I expected a fourth advantage once I asked for a one-sentence explanation. I did not get one, on any of the four products. Notes: [investigation-001](../investigations/investigation-001.md).
- On [DEF-002](../defects/DEF-002-Context-Loss.md) every recall still had Python and QA-NEEDLE-8841 after five unrelated turns. Some answers added a semicolon, a label, or "and the reference code is". The code never changed, so I left that as a format note.
- On [DEF-003](../defects/DEF-003-Hallucinated-Facts.md) the plain question already refused the company. Asking Perplexity for sources, or for yes/no/unknown, was not what stopped an invention. Those two prompts also passed. Notes: [investigation-002](../investigations/investigation-002.md).
- On [DEF-004](../defects/DEF-004-Ambiguous-Prompt.md) I did not file "Should I use Java?". Perplexity, Claude, and Gemini gave criteria or asked what is being built. One Claude run used a saved memory and the UI labeled it. ChatGPT Think stated a role, experience, a stack, and a project name on all three P-004-A runs, with no memory label. P-004-B labeled assumptions and dropped that context. I left that as a note. I could not see the source, so I did not call it an invented employer. Notes: [investigation-003](../investigations/investigation-003.md).
- On [DEF-005](../defects/DEF-005-Inconsistent-Behavior.md) all twelve chats said Canberra. The Perplexity source badge and the ChatGPT usage banner were not part of the answer.

Totals are in [Defect_Summary.md](Defect_Summary.md). What I would have raised if a run had failed is in [Risk_Assessment.md](Risk_Assessment.md).
