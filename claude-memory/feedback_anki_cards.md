---
name: feedback-anki-cards
description: "Rules for generating good Anki cards — full cloze coverage, no course-meta, no precise transient stats, minimal quote cards"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 555c7dfc-07f4-47bc-97e7-eeeb1789ab37
---

When generating Anki cards (basic Q&A or cloze deletion) for the user's studies, follow these rules. Established 2026-05-20 after the user reviewed the first ~200 cards I pushed.

**Why:** the user is building a long-term knowledge base via spaced repetition. Cards that survive 20 years of usefulness are good. Cards that test course-specific connective tissue, blank random filler words in quotes, or fixate on transient statistics are bad — they waste review time.

**How to apply** — for every card generated:

### 1. Cloze cards must blank EVERY conceptually distinct item in a list — AND choose the cloze numbering carefully

**Wrong (only one blanked):** `Sagan's three models are {{c1::security}}, domestic politics, and norms` — the answer's right there in the prompt.

**Two correct patterns, depending on what you want to test:**

(a) **Recall the whole set together — use the SAME `c1` for every item:**
```
Sagan's three models are {{c1::security}}, {{c1::domestic politics}}, and {{c1::norms}}.
```
Produces ONE card with all three blanks hidden simultaneously. The user has to remember all three. Best when the *list itself* is the unit of knowledge (Sagan's three models, Acharya's three mechanisms, the five critical lineages, etc.).

(b) **Recall each item individually with the others as context — use DIFFERENT cloze numbers:**
```
Sagan's three models are {{c1::security}}, {{c2::domestic politics}}, and {{c3::norms}}.
```
Produces THREE separate cards, each hiding one item with the other two visible. Best when each item is large enough to warrant its own card AND the surrounding items help disambiguate.

**Default to (a) — the user prefers set-recall for short lists.** If the list has long parenthetical explanations attached to each item, (a) becomes too hard and you should split into individual concept cards instead.

If a list resists either approach, **switch to a basic Q&A card**: *"What are Sagan's three models?"* → *"Security · domestic politics · norms."*

### 2. Cards must be course-agnostic — no "Week N" / "Lecture N" references in card content

The user wants knowledge that's useful in 20 years, not knowledge organised by *this specific course's syllabus*. Wrong: *"Three course through-lines closing out IRO: ..."* or *"Rodrik's trilemma runs through Weeks 8, 11, and 12."* Right: *"What is Rodrik's globalization trilemma?"* → *"Deep globalization + nation-state + democracy — pick any two."*

Deck names and tags can be course-specific (those are organisational metadata). **Card content cannot.**

### 3. Quote cards: minimal, and blank only load-bearing keywords

Most "memorise this quote" cards are low-value. Favour concept-definition cards instead. If a quote is genuinely exam-relevant (e.g. Clausewitz "war is the continuation of politics by other means"), blank only the **content keywords** — names, dates, technical terms, the punchline noun — not filler like "self-seeking individuals" or "very different pasts."

Rule of thumb: if a deleted word can be replaced by 3+ plausible synonyms without changing the quote's meaning, it's filler — don't blank it.

### 4. Skip transient or hyper-precise statistics

Statistics that pin down a specific report's numbers ("72% of humans under autocracy per V-Dem 2025") shouldn't be Anki cards. The user can re-look up the latest number when needed. What deserves a card is the **concept** (autocratisation wave; democracy in retreat globally), not the precise figure.

The exception: a number IS the concept. "9 nuclear-armed states" is conceptually load-bearing; "72% of the world under autocracy in 2024" is not. If you're uncertain, default to dropping the precise number from the card and using qualitative framing instead.

### 5. Prefer concept-definition cards as the dominant form

Best basic-card pattern: *"What is X?"* → 1–3 sentence definition. Best cloze pattern: a single sentence with the key term blanked, where the surrounding context lets a knowledgeable reader infer the term from the gap (i.e. the cloze is recall, not pattern-matching).

Avoid: comparison cards that depend on remembering both halves (split into two cards), cards that test course-arc connections (covered in rule 2), and cards built around the author's life facts (the user wants concepts, not biographies — unless the author IS the concept, e.g. "Clausewitz" as a discipline-defining figure).

### Where this applies

This applies anywhere I generate Anki cards — `/push-anki` skill, the `anki-from-reviews.js` batch parser, and any direct AnkiConnect pushes. The `push-anki` slash command's instructions should be updated to reference this feedback the next time the skill is edited.
