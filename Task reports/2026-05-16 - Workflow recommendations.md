# Workflow recommendations — 2026-05-16

*From a conversation where you asked: "What are some other ways you would recommend me to maximize workflow with you?" — saved so you can come back to it later.*

---

## "Check Box for Claude every once in a while" — honest answer

Within a single conversation, yes — I can revisit `Box for Claude.md` at natural break points (after finishing a task, when you ask "what's next"). That works.

**Across conversations, no — not reliably.** Each new conversation starts cold. Memory and preferences don't trigger actions; only the **harness** (Claude Code itself) can run things automatically. The two ways to make it actually automatic:

| Option | How it feels | Trade-off |
|---|---|---|
| **SessionStart hook** | Every new Claude Code session, I get the Box for Claude contents auto-injected. I'd open with "I see you added X — want me to start?" | One-time setup in `settings.json`. Adds ~10 lines to every conversation startup. |
| **Scheduled agent** (`/schedule`) | A cron-style routine that wakes Claude up on a timer (daily / weekly), reads the file, and acts on tasks | Runs even when you're not there. Costs more. Useful for "do this overnight." |

For your use case (you jot tasks in Obsidian, then later open Claude Code), **SessionStart hook is the better fit** — it surfaces tasks the moment you open me, with no extra typing.

---

## Other ways to maximize workflow

Ordered by likely payoff for *your* setup (non-technical, research-driven, wiki-based second brain):

1. **Skills / slash commands for your most-used wiki operations.** Your CLAUDE.md already defines `ingest`, `query`, `lint`, `new project`. These could be one-tap slash commands (`/ingest`, `/query`, `/lint`) so you don't have to re-explain the schema each time. Big friction reduction.

2. **A `state.md` per project, auto-read on session start.** Like Box for Claude but per-project: "currently working on X, blocked by Y, last thing I did was Z." When you open a session in indonesia-carbon-market, I'd already know the state. Pairs with the hook idea.

3. **Permissions allowlist.** Every time I run `git status`, `ls`, `find`, `node extract.js`, etc., you may get a permission prompt. The `fewer-permission-prompts` skill scans transcripts and proposes safe additions. Run it once and you'll see far fewer prompts.

4. **Scheduled weekly wiki lint.** Once a week, a routine runs `/lint` across all projects, posts a report. Catches stale claims and orphan pages before they accumulate.

5. **Use plan mode for ambitious tasks.** When you give me something big like the Project index task, hitting plan mode first lets you see and tweak the structure before I write 1000 lines. Saves rework.

6. **Be explicit about scope on first message.** "Just for week 4" vs. "for weeks 4–6" — your IRO request was perfect. The more I know upfront about depth and target audience (you, an examiner, future you), the less I over- or under-shoot.

7. **Tell me when I'm wrong, and *why*.** Memory works best when corrections are concrete ("don't summarize at the end, I read the diff"). Vague corrections get vague memories. You already do this well.

8. **Stop me early when I'm drifting.** Better to interrupt at minute 2 than let me finish 20 minutes of the wrong thing. There's no penalty.

---

## Open offers from that conversation

- Set up the **SessionStart hook** so I read `Box for Claude.md` automatically each new session.
- Start the **political-economy project index** task that's already sitting in Box for Claude (indonesia-carbon-market folder).

Let me know which (or both) when you come back to this.
