# deepseek-qa-audit

24 bugs found in DeepSeek LLM: logical errors, context loss, UX issues. Full bug reports and analysis.

# QA Audit: DeepSeek LLM

**Author:** Olga  Tsymbal
**Date:** May 2026  
**Background:** 6+ years in Quality Control, Training and Analytics (Yandex, T-Bank, Sber, Netmonet)

---

## Summary

Independent quality audit of DeepSeek LLM (large language model).  
**24 bugs** found, classified by type and severity.

**Key findings:**
- Logical errors (instruction misunderstanding)
- Context loss in long dialogues
- Contradictory advice (e.g., "sell X" → "buy X")
- UX issues (response visualization, data loss on send)
- Lexical errors (incorrect idioms in Russian)
- Inconsistent multimodal perception (faces detected, geometric shapes not)

---

## Why This Matters

LLM quality testing requires the same methodological approach as classic QC:  
requirements analysis → test case design → bug reporting → classification → recommendations.

This audit demonstrates that my 6+ years of QC experience (people, processes, metrics) is directly transferable to AI system testing.

---

## Bug Report Table

[Bug_report_DeepSeek.xlsx](Bug_report_DeepSeek.xlsx)

*(The table contains 24 bugs with reproduction steps, expected vs actual results, severity, and categories)*

---

## Bug Categories

| # | Category | Count | Examples |
|---|----------|-------|----------|
| 1 | Logical / Instruction Following | 4 | Confused "-тся" vs "-ться", ignored explicit instructions |
| 2 | Context Loss (long dialogues) | 3 | Forgot user's Ascendant (Scorpio → claimed it was Virgo) |
| 3 | Contradictory Advice | 2 | "Sell stock X" then "Buy stock X" |
| 4 | Hallucination / False Confirmation | 3 | Claimed to transfer context between chats, didn't |
| 5 | UX / Interface | 2 | Response stuck in "Thinking" block, data loss on send |
| 6 | Lexical / Russian Language | 2 | "Одета в пух и прах" (non-existent idiom) |
| 7 | Multimodal / Computer Vision | 2 | Faces detected, geometric shapes ignored |
| 8 | Technical Limitations | 3 | Can't read .docx without warning, Excel formula failed |
| 9 | Attribution Errors | 2 | Attributed user's own words to me |
| 10 | Other | 1 | ... |

---

## How to Reproduce (Example)

### Bug #1: Instruction misunderstanding in Russian test

**Steps:**
1. Ask: "В какой строчке все слова пишутся с -ТЬСЯ (мягкий знак)?"
2. Model answers based on "what does it do?" rule instead of following explicit instruction.

**Expected:** Model follows explicit instruction ("find -ТЬСЯ" = infinitive, soft sign).  
**Actual:** Model applies internal grammar rule ("-тся after "what does it do?").

**Severity:** High (core instruction following failure).

---

## Recommendations for DeepSeek Team

1. **Instruction priority** – Explicit user instructions should override internal grammar patterns.
2. **Context window warning** – Notify user when dialogue exceeds context limit.
3. **Honest "I don't know"** – Add ability to say "I'm not sure" instead of hallucinating.
4. **Multimodal consistency** – Either support geometric shapes or state unsupported clearly.
5. **File format handling** – Explicitly list supported formats (.txt, .pdf, .png, .jpg) and reject .docx with clear message.
6. **Cross-chat context** – Remove false promises about context transfer.

---

## Links

- **GitHub repository:** [[(https://github.com/akkershow/deepseek-qa-audit)](https://github.com/akkershow/deepseek-qa-audit)]
- **My LinkedIn:** [link if you have]
- **My resume:** [[link if you have](https://hh.ru/resume/84ba1c7cff0d8b25070039ed1f627433527762)]

## Contact

- **Telegram:** @akkershow
- **Email:** lachevskaya.olga@mail.ru

---

## License

This report is shared for educational and recruiting purposes.  
You may use it to improve DeepSeek or similar LLMs.

---

*Last updated: May 27, 2026*
