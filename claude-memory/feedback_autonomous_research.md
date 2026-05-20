---
name: Don't ask permission for non-destructive actions
description: User authorizes Claude to act without confirmation for anything that doesn't risk damaging their internal laptop files — web fetches, API probing, package installs, scratch folders, etc.
type: feedback
originSessionId: a375c951-2276-4c7a-8746-7e3b80ee55dc
---
Do NOT pause to ask "should I proceed" or "want me to do X" for actions that don't risk altering or destroying the user's existing files/system state. Just execute.

**Why:** User explicitly said "anything that's not gonna mess with my internal laptop files you can access without my permission" (clarifying an earlier "you dont have to ask me for permission, just go for it" during the Verra registry data-filling task). Confirmation pauses interrupt flow.

**How to apply:**
- Proceed without asking: web fetches, public API probing, npm/pip installs, creating scratch folders/files outside the user's project, reading public datasets, running scripts I authored, git operations on local-only branches.
- Still confirm before: destructive ops on their existing files (deletes, overwrites without backup), git push / force-push, git operations that rewrite shared history, sending messages or external API calls with side effects, anything irreversible.
- When in doubt about whether something modifies their files: make a backup first, then proceed.
