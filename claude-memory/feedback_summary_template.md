---
name: feedback-summary-template
description: "When writing exam/lecture summaries: definition table + 'Explained easily' callouts + one-page revision sheet at the end"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 555c7dfc-07f4-47bc-97e7-eeeb1789ab37
---

When the user asks for study summaries (lecture summaries, course summaries, exam prep), follow this structure. It was established for the IRO Week 4–6 summaries (May 2026) and the user explicitly asked me to keep using it.

**Why:** The user is non-technical and studies social sciences. Dense academic summaries don't build mental hooks. They need (a) **actual definitions** of every term they're expected to memorise, not just a list of terms, and (b) **plain-language anchors** at key moments that say *"this article/idea is basically about X"* so the concept sticks.

**How to apply:** For every summary you write for the user's coursework, do these two things on top of the normal deep-summary structure:

### 1. Glossary section gets actual definitions

Don't write a bullet list of terms expecting the user to know them. Build a **definition table** with three columns: Term | Definition | Source. Pull definitions from:
- The week's lecture slides first (most exam-relevant phrasing)
- The required readings second
- Authoritative external sources (UNHCR, IOM, canonical academic texts) where the week's materials don't define the term

Mark sources clearly. If a term isn't defined in the week's materials and you used external knowledge, say so ("not defined in lecture — added from canonical source").

### 2. "Explained easily" sections throughout

Add `> **Explained easily — [topic]:**` block-quote callouts at these points:
- **Once near the top of each summary** — a one-paragraph plain-language take on the whole week.
- **Under each required reading summary** — what is this article *doing*? What's the one-line take? Use everyday language and analogies. The goal is to create a mental hook so when the user sees the article title on the exam they immediately know "oh, that's the one about X."
- **Under any complex theoretical move** — Cox's problem-solving vs critical distinction, Hollifield's liberal paradox, Seth's three-part critique, Huysmans' securitization mechanism, etc. Give the user a "feel" for it before they hit the academic version.
- **Under contrast tables** — when two schools or thinkers are being compared, add a plain-language gloss explaining the actual difference in concrete terms.

Tone: clear, conversational, use analogies, no jargon. Like explaining to a smart friend who hasn't read the material. Two to five sentences is the sweet spot.

### 3. One-page revision sheet at the end

Every summary ends with a `## One-page revision sheet` section: a tight, scannable cheat sheet that captures the absolute essentials in one screenful. Structure:
- **Frame:** the one-sentence point of the lecture.
- **Definitions to nail / key concepts** as bulleted shorthand.
- **Key thinker(s) in one minute** — name + one-line contribution.
- **Key tables / lists** — preserve the most critical contrast tables compressed.
- **Lines to memorise** — 1–3 quotes the user should be able to drop verbatim.

The user explicitly loves these and asked them to be part of every summary. They get auto-aggregated into the course's review file (`*_review.md` under `wiki/projects/<course>/wiki/synthesis/`) by the `/extract-highlights` skill. IRO Weeks 4–6 are worked examples of the right tone.

### 4. Source citations: link to the specific page or location

When citing a source inline in synthesis files, summary files, or essay drafts, the citation should be **clickable AND specific**:
- For PDFs in the wiki: link to the file path with `#page=N` fragment (Obsidian-supported) so clicking the link opens the PDF at that page.
- Always include the **page number** in parentheses next to the source citation: `(ICAP 2025 factsheet, p. 4)` not just `(ICAP factsheet)`.
- For multi-author works the user knows well, short-name format is fine: `(Sunanda et al. 2025, §4.2)` for section references; `(Rodrik 2018, p. 19)` for page references.
- If the user is going to reuse the citation in an essay, both the link AND the page number matter — they need to verify the quote AND have the page for the final citation.

Example: instead of writing *"per ICAP factsheet"*, write *"per [ICAP 2025 factsheet, p. 4](../../raw/ICAP%202025%20-%20Indonesia%20NEK%20Trading%20Scheme%20factsheet%20104.pdf#page=4)"*.

### 5. Include survey data when present

For lecture summaries: if the lecture had an in-class survey, the survey results / framing experiment / takeaway is exam-critical content and MUST be included in the summary. The IRO Week 4 summary's in-class survey section is the worked example. Don't omit survey content — Denney in particular uses survey results pedagogically and they frequently appear on exams.

### Existing reference summaries

The IRO Week 4–6 summaries under `wiki/projects/finals-y2-s2/IRO/Summaries/` are the worked examples. Use their structure as the template for future summaries unless the user explicitly asks for something different.
