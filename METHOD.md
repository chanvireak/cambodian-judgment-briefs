# Method

How the 108 briefs were produced, and what was checked before a brief was accepted.

## Source

Judgments were selected from a private document library by document type (`Judgment`, 108 live
documents). Content is the library's OCR text of each Khmer judgment: space-segmented Khmer, no reliable page
structure, names sometimes reduced to a single initial or a bare digit.

Four of the 108 are **model judgments**: drafting specimens that carry editorial instructions ("a civil
judgment must be written on the points in Article 189 of the Code of Civil Procedure") and template
placeholders (`X`, `Y`, "house No. 00, street No. 00"). The rest carry the opposite stamp — "this is a real
case, not a model judgment". The specimens are briefed like any other document but marked `specimen, not
decided` in the header, and every count in this repository separates them from the 104 decided cases.

## Pipeline

Three stages, each idempotent, run by an AI agent with a small Python state machine.

1. **Prepare.** Fetch each document's OCR text, keep a character-exact copy, and emit a *numbered* working
   text: one sentence per line, `1. sentence`, split on the Khmer khan (`។`). The line number is the citation
   key. A per-document state file records the OCR checksum.
2. **Brief.** For each document: claim it (atomic claim file, so parallel workers cannot double-process),
   read the whole numbered text, write the five-point brief, then run the acceptance gate.
3. **Verify.** Re-run the gate over every accepted brief; regenerate the index and the digest.

## The citation scheme, and why

The obvious scheme — block labels such as `[FACTS 1]`, `[SC 3]` — was tested first and works only for
cassation-format judgments, because it keys off their fixed headings. On this corpus it produced citable
units for **1 of 108** documents; first-instance and appeal judgments produced none.

So the corpus uses sentence numbering instead: every brief cites `[Para N]`, N being the line number of the
numbered text. That works for every judgment, makes each cite checkable by eye in one file, and lets the
citation checker resolve all 5,602 cites mechanically.

## Acceptance gate (per brief)

A brief is only recorded as done if it passes both checks:

- **Structure** — H1 case title, a `Bench:` line in the header block, all five required sections present, at
  least one pin cite under each section, and a length between 200 and 1,000 words.
- **Cites** — every `[Para N]` resolves to an existing line in that document's numbered text; zero
  unresolved cites allowed.

A brief that fails either check is not recorded, is repaired, and is re-run. `reports/index.md` shows the
state of every document.

## What was deliberately not done

- **No repair of OCR damage.** Where the judgment gives one date in the facts and another in the reasoning,
  both appear in §6 of the brief. Where a name survived only as an initial, it stays an initial.
- **No outside research.** A brief states only what the judgment says. No commentary, no comparative law, no
  prediction.
- **No full-text publication.** Only structured notes and short quotes are published here.

## Cross-case digest

A parser reads every brief into a record (court, level, outcome, issues, ratio, defect note) and
writes computed tables; the analysis in `reports/digest.md` is authored prose kept in `reports/synthesis.md`
and spliced in on each run. Doctrine threads are grouped by rule, then by competing lines of authority, with
the cases named.

## Known weaknesses

- Outcome labels are heuristic (pattern-matched from the relief sentence) and were spot-checked, not audited
  case by case.
- The digest's doctrine flags are keyword-based; a case can be relevant without matching a flag.
- One AI model wrote all 108 briefs. Systematic misreadings, if present, are systematic.
