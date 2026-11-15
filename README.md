# Cambodian Civil Judgment Case Briefs

**108 five-point case briefs of Cambodian civil judgments (2015–2020), written by an AI agent from OCR'd Khmer court documents.** Research and study material — **not legal advice**. Corrections are welcome and expected.

---

## ⚠️ Read this before using anything here

- **Not legal advice.** Nothing in this repository is legal advice, an opinion on your case, or a substitute for a Cambodian lawyer. No lawyer–client relationship arises from reading or using it.
- **Machine-generated.** An AI agent read the OCR text of each judgment and wrote the brief below it. A language model summarised a noisy, machine-extracted Khmer document. Expect errors: misread figures, wrong party roles, a ratio that is really obiter, a missing argument.
- **Verify against the source.** Every brief carries pin cites in the form `[Para N]` pointing at sentence *N* of the machine-numbered judgment text. Those cites are machine-checked for *existence*, not for *correctness of the inference*. Open the judgment and read the cited sentence before relying on a statement.
- **Corrections are welcome.** If a brief misstates a judgment, open an issue with the doc id and the paragraph, or send a pull request. Disagreement about the law is fine too — say which case and which line.
- **Not maintained as a legal source.** This is a snapshot, not a citator. Judgments may be appealed, reversed or superseded; nothing here is updated for later developments.

## What is in here

| Path | What it is |
|---|---|
| `briefs/<doc-id>.md` | One brief per judgment, 108 files. Five points plus a disclosed-defects note. |
| `reports/digest.md` | Cross-case digest: corpus shape, doctrine threads, divergences worth arguing. |
| `reports/index.md` | Index of all 108 briefs with court, date and outcome. |
| `METHOD.md` | How the briefs were produced, the citation scheme, and the quality gates. |
| `DISCLAIMER.md` | The full disclaimer in one place. |

The underlying judgment texts are **not** published here. They are public court documents; only structured notes about them are reproduced.

## Scope

| | |
|---|---|
| Documents | 108 — **104 decided judgments and 4 model judgments** |
| Years | 2019 (98), 2020 (6); decided cases run 2019 – July 2020 |
| Courts | 16 — Phnom Penh (61), Kampong Thom (7), Siem Reap (6), Takeo (6), and 12 others |
| Level | 102 first instance, 1 appeal, 1 cassation, 4 drafting specimens |
| Subject | Mostly bank and microfinance debt recovery; also land, sale of immovable property, family, construction |
| Language | Khmer originals, English briefs, Khmer terms in parentheses where they matter |
| Pin cites | 5,602, all resolved against their source text |

**Four of the 108 files are model judgments, not decisions:** [160182](briefs/160182.md), [160204](briefs/160204.md), [160224](briefs/160224.md), [160264](briefs/160264.md). They open with drafting instructions — "a civil judgment must be written on the points in Article 189 of the Code of Civil Procedure" — and use placeholders (`X`, `Y`, "house No. 00, street No. 00"). The real cases in this library carry the reverse stamp: "this is a real case, not a model judgment". Their briefs say so in the header (`specimen, not decided`) and keep the drafting commentary in §6. Read them to see *how* a judgment is drafted; never cite them as authority for what a bench held.

Outcomes as recorded in the briefs: 93 money judgments for the claimant, 8 partly allowed, 5 dismissed, 1 allowed, 1 remanded on cassation.

**Only two of these decisions are appellate**, and the cassation judgment remanded without deciding the merits. Treat every doctrinal statement as trial-level reasoning, not binding authority.

## How each brief is structured

```markdown
# Party A v Party B (Judgment No., Court, Date)
Bench: N judges (president) · level · Doc ID

## 1. Facts
## 2. Legal issues            — phrased as questions
## 3. Arguments               — appellant/plaintiff and respondent/defendant separately
## 4. Judgment and reasoning  — outcome first, then the chain
## 5. Ratio decidendi          — the rule, stated for a future case; obiter listed separately
## 6. Source defects disclosed — OCR losses and internal contradictions, reported not repaired
```

The last section is the one to read first if you plan to quote a figure: it lists the dates, amounts and names that the judgment contradicts in different places, or that the OCR mangled.

## Privacy

Parties, children and counsel are reduced to initials (`Ms D`, `Mr C`, `(name redacted)`). Only judges are named, as they are named on the face of the judgment. Where the OCR had already lost a name to a bare digit, the brief says so rather than inventing one.

## License

MIT — see `LICENSE`. Applies to the briefs and the reports in this repository. The underlying judgments remain public court documents of the Kingdom of Cambodia and are not relicensed here.

## Citing this work

If you use it in research or a memo, cite it as *machine-generated research notes*, not as a source of law — e.g. "Case brief of Judgment No. 215 K (Supreme Court, 2020), AI-generated summary, verified against [Para 38]". Then cite the judgment itself.

---

Maintained by **Seng Chanvireak** ([@chanvireak](https://github.com/chanvireak)). Corrections welcome — see `CONTRIBUTING.md`.
