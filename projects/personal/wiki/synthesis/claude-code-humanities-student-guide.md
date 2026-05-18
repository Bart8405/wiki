---
tags: [productivity, claude-code, workflow, academia, humanities, anki, obsidian, zotero, indonesian, language-learning]
sources: []
updated: 2026-05-18
---

# Claude Code — A Humanities Student's Complete Guide

*How a 2nd-year International Studies student at Leiden can use Claude Code as a personal research assistant, writing partner, study tool, and language tutor.*

---

## Who this guide is for

This guide is written specifically for your situation: a student of international studies at Leiden University, headed to Indonesia on exchange, learning Bahasa Indonesia, focused on topics like GPE, IR, political economy, and Southeast Asian politics. Most AI guides online are written for software engineers. This one is not.

---

## Part 1 — Why Claude Code is different from the Claude website

When you open claude.ai in a browser, you get a chatbot. Each conversation is isolated — it forgets everything when you close the tab.

**Claude Code is different.** It runs in a folder on your computer (or in your wiki like this one). It reads files, writes files, and builds up memory across sessions. Think of it like the difference between hiring a tutor for one hour versus having a research assistant who works in your office, reads your bookshelves, and remembers everything you've discussed.

The specific superpower: Claude Code reads a file called `CLAUDE.md` at the start of every session. That file is your standing instructions — your preferences, your research focus, rules about how you want things done. Because it's a real file in your repo, it persists forever and travels with your work.

**For you, the key consequence**: the wiki you've already built (the one containing this file) is already a second brain. Every project folder has an `index.md` that Claude reads to know what you know. Over time, as you ingest more sources and write more pages, Claude becomes better at helping you — it knows your work, your projects, your research threads.

---

## Part 2 — Writing papers and essays

### The four-stage workflow

**Stage 1 — Planning.** Before writing a word, dump your assignment brief and your rough ideas into a conversation. Ask Claude to help you map an argument structure. It won't write your thesis for you — it will ask you the questions a good supervisor would ask: *What is your research question? What's the key tension you're resolving? What are the strongest counterarguments?*

**Stage 2 — Literature review.** Feed Claude a list of sources (or paste in abstracts). Ask it to identify:
- Themes across sources
- Debates or disagreements between authors
- Gaps that your paper could fill
- Missing perspectives (e.g. "which of these authors is writing from an Indonesian perspective rather than a Western one?")

**Stage 3 — Drafting.** Write a rough section yourself first — even badly — then ask Claude to help you tighten it. This order matters: write first, edit with AI second. If you let Claude draft from scratch, the writing won't sound like you and you won't learn.

**Stage 4 — Feedback.** Share a finished draft and ask for specific feedback: *Does the argument flow? Are there logical gaps? Is the evidence sufficient?* Ask it to steelman counterarguments your paper hasn't addressed.

### The Zotero integration (game-changer)

Zotero is the gold standard reference manager for humanities students. In 2026, you can connect Zotero directly to Claude using a tool called **Zotero MCP** (MCP = Model Context Protocol, the standard for giving AI access to external tools).

Once connected, you can say things like:
- "Find all the papers I've saved about carbon pricing in Indonesia"
- "Summarise the key arguments in my collection on ETS design"
- "What's missing from my reading list on Indonesian political economy?"
- "Format this citation in Chicago author-date style"

**How to set it up**: Install the `zotero-mcp` plugin from GitHub (search: `54yyyu/zotero-mcp`). It requires Zotero's local API to be running. No coding required — just follow the install guide. Once set up, tell Claude the MCP is available and it will use it automatically.

### What Claude cannot do for citations

Claude will format citations that *look* correct but often contain subtle errors — a wrong page number, a slightly wrong title. **Always verify citations against Zotero or the original source.** Use Claude to find and organise sources; use Zotero to be sure about the citation itself.

### Disclosure and academic integrity

Leiden and most Dutch universities now require you to disclose AI use. The current standard is to describe *what* you used AI for, not just that you used it. "Used Claude Code to assist with literature search and structural feedback on drafts" is a complete, honest disclosure. AI-assisted outlining and editing is no different in principle from having a writing tutor read your draft — but be honest about it.

---

## Part 3 — Knowledge management and your second brain

You're already using Obsidian and this wiki. Here's how to make the most of the system you have.

### The Karpathy pattern (you're already using it)

This wiki is structured on the LLM wiki pattern described by Andrej Karpathy (AI researcher): raw sources go in `raw/`, Claude-maintained pages go in `wiki/`, each project has its own `index.md` so Claude always knows what you know. This is the best-known pattern for building a queryable knowledge base with Claude Code.

The key habit is **ingesting** new sources as soon as you read them. When you find a good paper or article, run the `ingest` operation and write a summary page. Over a year, your wiki becomes a personal encyclopedia of everything you've read, queryable in seconds.

### How to use your wiki for paper writing

When you're starting an essay, instead of starting from scratch, say: "I'm writing about X. Read my project index for `indonesia-carbon-market` and `thematic-seminar-essay` and tell me what I already know about this topic."

Claude will synthesise across everything you've ingested and give you a structured starting point. You're literally mining your own past research.

### Cross-project linking

When themes appear in multiple projects — for example, "political connections in the Indonesian carbon market" appears in both your carbon market project and your thematic essay — use cross-project links. This is especially useful when Bart's Indonesia research and your studies start to overlap with each other over time.

### The inbox habit

High-productivity researchers (both humanities and STEM) use an inbox capture habit:
1. When you read something interesting — an article, a tweet, a lecture slide — dump a quick note into an `inbox/` folder.
2. Periodically (weekly), run a Claude session to process the inbox: summarise each note, file it into the right project, and find connections to existing pages.

This keeps your wiki growing without requiring you to write perfect notes in the moment.

---

## Part 4 — Anki and spaced repetition

Spaced repetition (the system Anki uses) is one of the most well-researched study techniques in cognitive science. The problem is that making good flashcards is slow. Claude solves this.

### Connecting Claude Code to Anki

Install the **Anki MCP server** (search: `ankimcp.ai` or `johwiebe/anki-mcp` on GitHub). This connects Claude Code directly to your Anki desktop app. Once connected:
- Claude can create new cards and add them directly to a deck
- Claude can query which cards are due for review
- Claude can generate cards in bulk from source text

### The workflow

1. You ingest a lecture PDF or reading into your wiki.
2. After the ingest session, say: "Generate 15 Anki flashcards from this reading in cloze format and add them to my `Indonesia Political Economy` deck."
3. Claude creates the cards, adds them to Anki, and you review them tonight.

For your subjects (GPE, IR, political economy), the best card types are:
- **Cloze deletions**: "The Indonesian ETS launched in {{c1::2023}} under the NEK framework"
- **Concept definitions**: "What is rent-seeking? → When actors use political connections to capture economic benefits rather than creating value"
- **Case-based**: "Which Indonesian forest carbon project was suspended in 2021 and why? → [Rimba Raya; REDD+ methodology dispute]"

### Anki for Bahasa Indonesia

This is where Anki really shines. Create a `Bahasa Indonesia` deck. Have Claude generate vocabulary cards from:
- News articles you read in Indonesian
- Vocabulary from your exchange prep materials
- Field-specific terms (political science vocabulary in Indonesian)

---

## Part 5 — Learning Indonesian with Claude Code

You're learning Bahasa Indonesia ahead of your exchange. Claude is a surprisingly good language tutor.

### Using Claude as a conversation partner

Set up a project note (in CLAUDE.md or a conversation) that says: "I am learning Bahasa Indonesia at [your level]. When I write in Indonesian, correct my grammar and vocabulary mistakes. Explain why something is wrong, not just what's correct."

You can then:
- Write journal entries in Indonesian and get corrections
- Practice formal Indonesian (suitable for academic settings) vs. informal Bahasa
- Ask Claude to translate something and then ask it to explain why it chose certain words

### The "Fluent" plugin for Claude Code

A tool called **Fluent** (GitHub: `m98/fluent`) turns Claude Code into a structured language tutor using spaced repetition and progress tracking. It uses proven cognitive science methods: spaced repetition, active recall, and adaptive difficulty. It tracks which vocabulary you struggle with and revisits it.

### Indonesia-specific vocabulary

Ask Claude to help you build:
- A vocabulary deck of Indonesian political and government terms
- Phrases useful for conducting interviews (for future field research)
- Academic reading vocabulary (journal abstracts are often in Indonesian)

### Connecting language to your research

When you read an Indonesian-language government document (like SRN PPI filings), have Claude:
1. Translate it
2. Explain field-specific terminology
3. Add new terms to your Anki deck

This turns your research into language learning and vice versa.

---

## Part 6 — Staying current: news and geopolitics

For someone focused on Indonesia, SEA, and geopolitics, keeping up with news and connecting it to academic frameworks is a daily task.

### The news-to-wiki pipeline

Build a habit of:
1. Reading news (Reuters, The Diplomat, Jakarta Post, Nikkei Asia, SCMP for China-SEA)
2. When something connects to your research, paste it into Claude with: "Summarise this article in 3 bullet points and identify which of my existing wiki concepts this connects to."
3. Claude suggests connections and you decide whether to add a note to your wiki.

### Building a reading list

Ask Claude to help you identify the key journalists and scholars to follow on:
- Indonesian political economy
- Southeast Asian geopolitics
- Global carbon markets and climate policy

Claude can also help you set up RSS feeds or newsletter subscriptions for these sources.

### Connecting news to theory

This is a distinctly humanities skill and Claude is particularly good at it. When something happens in Indonesia, ask: "How does this relate to the concept of rent-seeking / developmental state / principal-agent problem?" Claude will walk through the connection and you can test your own interpretation against it.

---

## Part 7 — Exam preparation

You've already seen this in the study plan Claude created for your May exams. Here's the reusable pattern:

### The 5-step exam prep workflow

1. **Input your syllabi**: give Claude your lecture list, key readings, and exam format.
2. **Build a revision schedule**: Claude maps topics to days with built-in review cycles.
3. **Generate practice questions**: "Write 10 short-answer questions on the lecture about realism in IR theory, at the difficulty level of a Leiden BA exam."
4. **Test yourself**: answer the questions yourself, then ask Claude to evaluate your answers and point out gaps.
5. **Anki integration**: turn difficult concepts from practice questions into Anki cards for last-day review.

### For conceptual subjects (IR, GPE, PoS)

Ask Claude to create "concept maps" — structured outlines of how different theories, concepts, and case studies relate to each other. This is better than just reading notes because it forces synthesis.

---

## Part 8 — Integration with your other tools

### The ecosystem you should build

```
Zotero (reference manager) ←MCP→ Claude Code
                                        ↓
Obsidian/Wiki (your notes)         Processes sources,
                                   writes wiki pages,
                                        ↓
Anki (flashcard review) ←MCP→  generates Anki cards
```

### n8n for automation (advanced)

Once you're comfortable with Claude Code, consider **n8n** (free, self-hosted automation tool). It lets you build workflows like:
- "Every time I save a PDF to my Downloads folder, automatically ingest it into my wiki"
- "Every morning, fetch the Jakarta Post headlines and add a briefing to my wiki inbox"

This is what researchers at bigger institutions pay for in tools like Elicit or Lateral — you can build it yourself for free.

### Logseq as an alternative to Obsidian

If you find Obsidian's plugins overwhelming, Logseq is a simpler alternative with built-in daily notes and graph view. It has a similar Claude Code integration path.

---

## Part 9 — Learning from others on the same path

### Science and AI students you can learn from

The most useful role models for your workflow are actually not other humanities students (who haven't adopted these tools yet) but:

1. **PhD students in computational social science**: they combine qualitative humanities skills with data tools. Follow `@brettaylor` and similar on X/Twitter for workflow ideas.
2. **AI researchers who write** (Andrej Karpathy, Simon Willison): their public wikis and note systems are the origin of the Karpathy pattern this wiki uses.
3. **Science journalists**: people who process high volumes of complex information and translate it for general audiences. Their reading/filing habits are highly transferable.

### The Leiden context

You're ahead of most of your peers. In 2026, humanities students are still "early adopters" of these tools — Anthropic's own research shows STEM students integrated Claude earlier. Your advantage: you can build a more sophisticated workflow now, before these tools become standard, which means you'll be better at using them by the time everyone else starts.

---

## Part 10 — Practical setup checklist

### Do now (30 minutes)

- [ ] Install **Anki** if you haven't (free at apps.ankiweb.net)
- [ ] Install the **AnkiConnect** add-on (required for MCP integration; add-on code: `2055492159`)
- [ ] Create a `CLAUDE.md` in your wiki root that tells Claude your background and preferences (name, field, research focus, output style preferences)
- [ ] Set up one Anki deck per subject: `GPE`, `IR Theory`, `Indonesian Politics`, `Bahasa Indonesia`

### Do this week

- [ ] Set up **Zotero MCP** — follow the `54yyyu/zotero-mcp` guide on GitHub. Takes about 20 minutes.
- [ ] Build the inbox habit: create an `inbox/` folder in your wiki and put raw notes there after lectures
- [ ] Try one Anki card generation session from a lecture reading

### Do before exchange

- [ ] Build a `Bahasa Indonesia` Anki deck using Claude to generate cards from your study materials
- [ ] Create a `field-research` project in your wiki to capture observations from Indonesia
- [ ] Set up a "news briefing" prompt: save a Claude prompt that, when run, ingests recent Jakarta Post / The Diplomat headlines and files relevant stories into your wiki

---

## The one principle underlying all of this

**Claude Code amplifies consistency, not intelligence.** The more consistently you ingest sources, make Anki cards, and maintain your wiki, the smarter your second brain gets. A researcher who uses Claude Code inconsistently for six months will be outperformed by one who uses it consistently for three months. Build small habits, not complex systems, and let them compound.

---

*Guide compiled from: Anthropic education research, second-brain community (noahvnct.substack.com, aimaker.substack.com), Anki MCP documentation, Zotero MCP community, Fluent language learning plugin, PKM research (atlasworkspace.ai).*
