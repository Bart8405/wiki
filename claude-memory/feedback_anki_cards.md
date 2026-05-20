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

### 6. Keep answers TERSE — but readable; drop filler, fragments over full sentences

Match the user's own card style (observed across 13,000+ user-made cards in MATURITA / Every_fucking_day decks). His pattern:
- **Answers are single-line, often just bullet-style:** "Zoon Politikon, Organon, Metafyzika, Etika..." or "Best alternative to a negotiated settlement - you should compare X to Y - stronger BATNA = stronger position"
- **Separators:** ` - ` (hyphen with spaces) between linked ideas; `+` for paired items; commas for simple lists; parentheticals for clarifications
- **No padding.** Drop "essentially", "in this context", "the idea is that", "fundamental basis of", "characteristic mode of".
- **Fragments fine.** "Goal: X" beats "The approach aims to understand X."
- **Don't over-use unicode symbols.** ↔ `=` `·` etc. CAN be used sparingly when they save real words (e.g. `democracy ↔ autocracy`). DON'T sprinkle them throughout — they hurt readability when used as decoration. The user complained the over-symbolised version was "hard to orient in."
- **Words first; symbols only when they genuinely speed reading.** If you find yourself adding ↔ between every pair, you're overusing them.

**Example transformation (revised after iteration with user):**

*Verbose (avoid):* "The idiographic approach aims to understand the particular — the unique characteristics, meaning, and context of a specific case, event, person, or text. It is the characteristic mode of the human sciences (history, literary studies, philosophy)."

*Over-symbolised (also avoid — too dense):* "Goal: understand the *particular* — unique features / meaning / context of a single case (event, person, text). Mode of the human sciences (history · literature · philosophy). Windelband (1894): natural ↔ human science divide = a choice of *approach*, not *topic* — the same object (a society, a psyche) can be studied either way."

*Good (do this):* "Understanding the unique features and context of a specific case (event, person, text). Mode of the human sciences — history, literature, philosophy. Opposite: nomothetic (universal laws)."

The good version uses real words, single hyphen separators, plain prose. Symbols only where helpful.

### 7. Use **bold** for emphasis, NOT CAPS

CAPS are harder to read in Anki than bold. `**important**` beats `IMPORTANT`. Already-bolded important terms in the surrounding text help orient the reader to what matters. Reserve CAPS for the *very* occasional load-bearing single word, never for whole phrases or contrasts.

### 8. One concept can have MULTIPLE cards — but each must have a DISTINCT angle

It's fine to have 2-3 cards about a single concept. **NOT fine to have 2 cards with near-identical Q&A.** Distinct angles:
- *Definition* card: "What is X?" → 1-line definition
- *Example* card: "What's a textbook example of X?" → the case
- *Application* card: "How does X explain Y?" → mechanism
- *Contrast* card: "X vs Y — what's the difference?" → key difference in one line

If two cards I generate end up with the same answer, **dedupe** — keep one, change the other to a different angle, or drop it.

### 9. Question must match the answer's scope

If the question is "What is X + Y + Z?", the answer must cover X AND Y AND Z. Don't ask multi-concept questions with a single-concept answer.

When the source content has a combined header like "induction + deduction + ampliative reasoning," **split into separate cards** — one for each concept. The combined header in the wiki is for indexing convenience, not a contract that the cards must follow the same combination.

### 10. Deduplicate at the concept level — not the highlight level

The wiki review files may have multiple highlights for the same underlying concept across different lectures or sections. When generating Anki cards, dedupe at the **concept** level. Don't create one card per highlight if the same concept is being highlighted in multiple places.

Specifically: when I parse `### TermName` entries from review files, group by canonical concept first, then generate ONE card per concept (with multiple "Seen in" sources). Don't blindly map one entry → one card.

### 11. Cloze recreation: when converting `c1/c2/c3` to all-`c1`, DELETE the note and re-add it

If you just edit the text of an existing cloze note (changing `{{c2::X}}` to `{{c1::X}}`), Anki keeps the old card slots for `c2`, `c3`, etc. — these become **empty cards** that show up in review with "No cloze 2 found on card" warnings. The user has to run Tools > Empty Cards manually to fix.

**Correct procedure for cloze-renumbering:**
1. Read the note's current text, tags, and deck via `notesInfo`.
2. **Delete** the note via `deleteNotes`.
3. **Add** a fresh note via `addNote` with the new text → Anki creates exactly the right card slots.

This loses review history, which is acceptable for recently-pushed cards. For cards with significant review history (mature intervals, many lapses), prefer leaving them alone or asking the user before recreating.

### Where this applies

This applies anywhere I generate Anki cards — `/push-anki` skill, the `anki-from-reviews.js` batch parser, and any direct AnkiConnect pushes. The `push-anki` slash command's instructions should be updated to reference this feedback the next time the skill is edited.
