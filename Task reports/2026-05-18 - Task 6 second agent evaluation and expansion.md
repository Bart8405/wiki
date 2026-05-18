# Task Report — Task 6: Second Agent Evaluation and Expansion

**Task number**: 6  
**Date**: 2026-05-18  
**Agent**: 7AM fallback agent  
**Deliverable**: This report (evaluation + expansion of Task 5 guide + critical assessment + future prompt advice)

---

> **Thank you to Agent 1!** You did solid, specific work and left this task cleanly untouched. The guide you wrote is genuinely better than 90% of "use AI for studying" advice online — because you named real tools rather than vague categories, and because the checklist at the end is actually doable. I'll try to build on what you started rather than repeat it.

---

## Part 1 — What the first agent got most right (the crucial findings)

Of everything in Agent 1's guide, these are the three findings that will have the biggest real-world impact for you:

### 1. "Write first, AI edits second" (the most important principle in the whole guide)

Agent 1 mentioned this in Part 2 almost in passing, but it deserves to be in bold at the top of the guide. The single biggest mistake students make with AI writing tools is asking the AI to draft *from scratch*. If you do that, you get a plausible-sounding essay that doesn't sound like you, doesn't reflect your actual thinking, and you don't learn anything from writing it.

The right sequence is: **you write a bad first draft → Claude improves it → you revise Claude's version → you submit your version.**

This matters especially for Leiden, where tutors read dozens of essays and will notice when writing doesn't sound like a student. More importantly, it matters for your own development: you're at Leiden to learn to think and argue, not to produce outputs.

### 2. Zotero MCP is the highest-ROI setup (and it's free)

This is Agent 1's biggest concrete find. Right now your research workflow probably looks like: find paper → save to Zotero → open Zotero → manually find citation → paste into Word/Obsidian. With Zotero MCP, it looks like: find paper → save to Zotero → ask Claude "find everything I've saved about Indonesian ETS" → Claude gives you a synthesised summary with citations ready to use.

For a student doing a literature-heavy thesis (which you will be), this is a genuine multiplier. Prioritise this setup above everything else in Agent 1's checklist.

### 3. You are ahead of your peers right now — but the window is closing

Agent 1 cited Anthropic's own research showing humanities students are still early adopters in 2026. This is a real and time-limited advantage. The students building these workflows now will be the ones who write better theses, process more literature, and hit the job market with demonstrated research skills. This advantage disappears as these tools become standard — probably within 2-3 years. Use it now.

---

## Part 2 — Expanding on what Agent 1 covered

### On the CLAUDE.md (Agent 1 said "write one" but didn't show you how)

A `CLAUDE.md` file is the single most valuable thing you can maintain in your wiki. It's what makes every Claude session feel like continuing with someone who knows you, rather than starting from scratch with a stranger.

Agent 1 told you to create one — here is a starting template you can copy, paste, and modify:

```markdown
# About Bart

I am a 2nd-year BA International Studies student at Leiden University (Netherlands).
My research focus: political economy of the Indonesian voluntary carbon market.
Going on exchange to Indonesia in [semester].
Learning Bahasa Indonesia (current level: [beginner/intermediate]).

## Key research projects
- **indonesia-carbon-market**: My main research project. Focus on REDD+, NEK framework,
  IDX Carbon, political connections in project ownership.
- **thematic-seminar-essay**: Essay on carbon pricing in Indonesia (ETS vs carbon tax).
- **finals-y2-s2**: Exam prep (completed May 2026).
- **personal**: Workflow, language learning, and general notes.

## How I want Claude to work with me
- Write in plain language. Define terms on first use.
- When I ask for a summary, give me bullet points, not paragraphs.
- When I ask for feedback on writing, be direct — tell me what's wrong, not just
  what's good.
- When I ask a research question, tell me if you're uncertain rather than
  making something up.
- I prefer short, frequent outputs over long walls of text.
- I care about academic integrity — don't write my essays, help me think.

## Tools I use
- Obsidian (notes and wiki)
- Zotero (references) — [MCP connected / not yet connected]
- Anki (flashcards) — [MCP connected / not yet connected]

## Style preferences for wiki pages
- YAML frontmatter with tags, sources, updated date
- Start every page with a one-line italic summary
- Lowercase, hyphen-separated filenames
```

Edit this to match your actual situation and save it at `/home/user/wiki/CLAUDE.md` (the root level — it already exists but you can update it). Every Claude Code session reads it first.

### On Anki: specific card types for your subjects

Agent 1 gave good general advice. Here are concrete examples for your specific subjects:

**For GPE (Global Political Economy):**
- "What does the 'race to the bottom' thesis predict about carbon pricing in developing countries? → That competitive pressure for foreign investment causes governments to keep environmental standards low to attract industry."
- "Name one empirical case that challenges the race-to-the-bottom thesis → [your answer based on your readings]"

**For IR Theory:**
- "What is the key difference between neorealism and neoliberal institutionalism on international cooperation? → Neorealism: states care about relative gains (what I gain vs you); neoliberalism: states care about absolute gains (what I gain)"
- "Which IR theorist coined the concept of 'complex interdependence'? → Keohane and Nye, 1977"

**For Indonesian carbon market (ongoing research):**
- "What does 'NEK' stand for in Indonesia's carbon framework? → Nilai Ekonomi Karbon — the 2021 presidential regulation establishing the national carbon pricing framework"
- "Which Indonesian ETS began trading in 2023? → IDX Carbon (the Indonesia Stock Exchange's carbon trading platform)"

The key for IR/GPE flashcards is always: **concept → definition + one example**. Not just "what is X" but "what does X predict/explain, and name a case."

### On Indonesian language learning: beyond vocabulary

Agent 1 covered vocabulary flashcards. Here are two more advanced techniques:

**1. "Translate and explain" sessions:** Find an Indonesian-language document relevant to your research — a government press release, a news article from Tempo or Kompas — and paste it into Claude with: "Translate this, but also explain any technical or political jargon in plain language, and flag any phrases that would sound different in formal vs. informal Indonesian."

This is more useful than a dictionary because it teaches you how Indonesians actually communicate about policy, not just individual word meanings.

**2. Shadowing preparation:** Before your exchange, take any audio from Indonesian news (TVRI, Metro TV on YouTube) and have Claude process a transcript. Use it to study pronunciation patterns and sentence rhythm — both things flashcards don't teach.

---

## Part 3 — Ideas Agent 1 didn't cover (new territory)

### 1. The "pre-mortem" before you submit an essay

Before submitting any essay, paste the final draft and ask: *"You are a Leiden University tutor grading BA essays. What are the three most likely reasons this essay would receive a 6 rather than an 8? Be specific."*

This is more useful than asking "what's good about this essay" — tutors aren't looking for good things, they're docking points for problems. Getting Claude to simulate that grader's mindset before submission is one of the highest-value things you can do.

### 2. Citation network analysis (for your thesis and seminars)

When you're building a literature review, you want to know: who are the key thinkers in the field, who cites whom, and which debates are central vs. peripheral?

Ask Claude: *"Based on the sources I've saved in Zotero about Indonesian carbon markets, build me a map of the key scholars and what each one argues. Then tell me which two scholars most directly disagree with each other."*

This replaces hours of manually reading through citations and gives you a structure for your lit review before you write a word.

### 3. The "rubber duck" workflow for building your own arguments

When you're stuck on an argument — not sure if it holds together — use Claude as a thinking partner, not a writing partner. Explain your argument out loud (or in text) as if you were explaining it to a smart friend who doesn't know the field. Then ask: *"What's the weakest part of that argument? Where would a skeptical reader push back?"*

This is the "rubber duck debugging" technique from software engineering, applied to essay writing. The act of explaining forces you to find the gaps, and Claude will point to what you missed.

### 4. NotebookLM for document-heavy research

Google's NotebookLM (free) does something Claude Code doesn't: it lets you upload a batch of PDFs and then generates an AI-hosted "podcast" discussion of them — two synthetic voices discussing the key themes, debates, and gaps. 

This sounds gimmicky but has a real use: listening to a 15-minute audio summary of five dense papers while walking to campus is a genuinely efficient way to get the shape of a literature before you read it in depth. Use it as a pre-reading filter — it helps you decide which papers to read carefully vs. skim.

### 5. Building a field research journal before your exchange

Create a `field-research` project in your wiki now, before you go to Indonesia. Set up:
- `raw/pre-departure/` — for documents you collect before leaving (government registries, company filings, maps, directories)
- `wiki/entities/` — for people and organisations you want to learn about in Indonesia
- A CLAUDE.md entry saying: "I am preparing for research fieldwork in Indonesia. Help me structure observations, interviews, and field notes."

When you're in Indonesia and something interesting happens — a conversation, a document you photograph, an observation — you can ingest it into this project immediately. By the time you return, you'll have a structured archive of field notes rather than a pile of phone photos and memory.

### 6. Using Claude for bureaucratic Indonesian documents

Your research involves reading documents like SRN PPI filings, KLHK permits, and NEK presidential regulations. These are written in formal Indonesian bureaucratic language (*bahasa birokrasi*) that is different from conversational Indonesian and very hard to parse even for fluent speakers.

Claude is good at this. Paste in a document and ask: *"This is a formal Indonesian government document. Translate it, and then summarise what it requires each party to do, in plain language."*

This is a research skill that will separate good political economy analysts from average ones — most researchers skip primary documents and rely on secondary sources that may misrepresent them.

### 7. Perplexity AI as a complement to Claude Code (not a replacement)

Perplexity (free tier exists) has real-time web access and gives source citations for everything it says. Use it for the initial discovery phase — "what are the three most recent academic papers on Indonesian ETS design?" — then bring those findings into Claude Code for deeper analysis.

Think of the workflow as: **Perplexity finds → Claude Code analyses → your wiki stores.**

Claude Code on its own doesn't have real-time web access for every task; Perplexity fills that gap.

### 8. The "exchange readiness" audit

One month before your Indonesia exchange, run this session: paste your exchange programme details, your research questions, and your current wiki index into Claude and ask: *"What do I still need to learn or prepare before arriving? What gaps exist in my knowledge of Indonesian politics, culture, and language that could affect my research or daily life?"*

This turns your existing wiki into a gap analysis rather than just an archive.

---

## Part 4 — Critical assessment of Agent 1's work

This is honest feedback on what was good and what could have been better.

### What was genuinely good

**Specificity over generality.** Most "use AI for studying" guides say things like "AI can help with writing" and leave it there. Agent 1 gave you real GitHub repo names, add-on codes, and step-by-step action items. That is the difference between advice you can act on and advice that sounds good but goes nowhere.

**The writing workflow principle.** Telling you to write first and have AI edit second is the single most important practical guidance in the whole guide, and it's correct. This is a principle worth revisiting every semester.

**The setup checklist.** Ordered by effort and priority, short enough to actually do. Good format.

**Tone.** Clear, non-technical, not condescending. Matched what you asked for.

### What could have been better

**1. It didn't verify tools before recommending them.**

Agent 1 mentioned `m98/fluent` (the Fluent language plugin) and `54yyyu/zotero-mcp` as if they're definitely working and maintained in 2026. Tool landscapes change fast — a GitHub repo mentioned as "great" in a blog post from 6 months ago may be unmaintained or broken. Before recommending a tool, I would have checked if the repo had been updated recently and whether users were reporting issues. Agent 1 didn't do that.

**Consequence for you:** Before installing either of these, check the GitHub repo directly. Look at: last commit date, open issues, number of stars. If the last commit was a year ago and issues are piling up unanswered, pick an alternative.

**2. It assumed desktop Claude Code, not web Claude Code.**

This session is running in a remote, cloud-based environment — not on your local computer. The Anki MCP and Zotero MCP integrations that Agent 1 described require the Claude Code CLI running locally (so it can reach your local Anki/Zotero). That's a non-trivial setup difference that wasn't flagged.

**Consequence for you:** If you're primarily using Claude Code through the web interface (claude.ai/code), the local MCP integration won't work directly. You'd need to set up Claude Code as a CLI on your own laptop. That's worth doing, but it's a bigger step than the guide implied.

**3. It gave you a list when you might have wanted a priority.**

The guide has 10 parts and covers everything from n8n automation to Logseq to NotebookLM. That's comprehensive, but for a student who's about to sit exams and go on exchange, it can feel overwhelming. A cleaner output might have been: "Here are the 3 things that will have the most impact. Do those first. Here are the other 7 for later."

**4. It didn't use your existing wiki as evidence.**

Agent 1 could have looked at your actual projects — `indonesia-carbon-market`, `thematic-seminar-essay` — and said: "Look, you already have X pages about Y. Here's a specific thing Claude could help you do with what you've already built." Instead, the guide is generic (good for any humanities student) rather than tailored (great for Bart specifically).

**5. The cited sources are low-authority.**

The bottom of the guide cites `noahvnct.substack.com`, `aimaker.substack.com`, and `atlasworkspace.ai`. These are newsletters and blogs — not primary sources. Anthropic's own documentation (docs.anthropic.com) and Claude Code's official documentation would be more trustworthy starting points.

---

## Part 5 — How to get even better work from future agents

This is the most actionable section. Small changes to how you write tasks produce large improvements in what agents produce.

### 1. Lead with the specific deliverable, not just the topic

**What you wrote:** "write me a comprehensive guide on how I can use Claude Code in the best way"

**What would work better:** "Write a practical, prioritised guide — not more than 8 sections — on using Claude Code as a humanities student. Each section should include at least one example prompt I can copy and paste. The highest priority is Anki and Zotero integration."

When you specify format, length, and priority, the agent doesn't have to guess — and guessing is where quality drops.

### 2. Tell the agent what you already know

If you tell Agent 1 "I already use Zotero daily but have never used Anki," the guide focuses on Anki setup and treats Zotero as known context. Instead, Agent 1 had to guess your baseline and defaulted to explaining everything — which makes the guide longer and less targeted.

**Template:** "Assume I know: [X, Y, Z]. I don't know yet: [A, B, C]. Focus on the gap."

### 3. Ask for verification of tool recommendations

Add a line like: "Before recommending a tool, check that it is actively maintained (last GitHub commit within 6 months) and note if it requires a paid subscription."

This forces the agent to verify rather than hallucinate tool names that sound plausible.

### 4. Specify "concrete examples" explicitly

Adding "include at least one concrete example for each recommendation" dramatically improves output quality. Agents default to generic advice when you don't ask for examples — they have to be pushed toward specificity.

### 5. The two-agent architecture (what you already do) is smart — make it explicit

Your 2AM/7AM setup works because the second agent has no sunk cost in the first agent's choices and can critique them honestly. Keep this pattern.

To make it even more effective: have the first agent explicitly flag its uncertainties. At the end of the Task 5 guide, Agent 1 could have written "I am not certain that `m98/fluent` is still maintained — please verify." That would have saved you from following potentially broken advice.

**You can instruct this:** Add to the task description: "At the end of the report, list any claims you made that you are less than 90% confident about."

### 6. Give the agent a persona or role that matches the task

Instead of "write me a guide," try: "Imagine you are a second-year PhD student in political science who uses Claude Code daily for research. Write a guide for your first-year undergraduate mentee who is just getting started."

Giving the agent a clear perspective produces more grounded, experience-based advice.

### 7. Break big tasks into explicit phases

Task 5 was one long task ("write a comprehensive guide"). That leaves the agent to decide what "comprehensive" means and how to structure it. A better format:

> "Phase 1: Search for the top 5 tools that humanities students use with Claude Code and verify each one is real and maintained.  
> Phase 2: Write a structured guide using only the verified tools.  
> Phase 3: Write a 5-item action checklist prioritised by impact."

Phased tasks are harder to botch because each phase has a clear success criterion.

### 8. Ask for a "what I would have done differently" note from the agent

At the end of any task, add: "After you complete this, write one paragraph on what you would have done differently if you had more time or better information."

This self-reflection forces the agent to identify its own weaknesses, which helps you calibrate how much to trust the output.

---

## Summary

Agent 1 produced a genuinely useful guide — specific tool names, a practical checklist, good tone. The most important things it got right: write first, AI second; Zotero MCP is the highest-ROI setup; you're ahead of your peers right now.

The main gaps I've tried to fill: a concrete CLAUDE.md template you can copy, the "pre-mortem" essay technique, NotebookLM for audio summaries, field research setup for your exchange, and the distinction between web Claude Code and CLI Claude Code (which affects MCP setup).

The most important future improvement: be specific about the deliverable format when you write tasks, and ask agents to verify tools before recommending them.

---

*Written by: 7AM fallback agent (Task 6).*
