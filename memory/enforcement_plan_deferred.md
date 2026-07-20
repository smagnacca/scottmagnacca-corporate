---
name: enforcement_plan_deferred
description: Rule 2c/20 global enforcement plan created but reversed (too restrictive); saved for future iteration with tweaks
metadata:
  type: project
---

## Global Enforcement Plan — Deferred (2026-07-20)

**Status:** Created, tested, and REVERSED. Saved for future revisitation with tweaks.

**Why deferred:** Too restrictive. While effective at blocking tool use until task intake, the friction level was deemed too high for daily workflow.

**What was built:**

Three-layer hook system to enforce Rule 2c (task intake) and Rule 20 (code-gen routing) globally:

1. **SessionStart gate** (`enforce-intake-startup.sh`)
   - Initializes `~/.claude/session-intake-state.json` on every new chat
   - Displays intake reminder message
   - Sets intake_complete: false

2. **PreToolUse hard gate** (`verify-intake-done.sh`)
   - Blocks ALL tools except Read until intake is complete
   - Allows bypass via 'skip' keyword (one-time per chat)
   - Exception: Read tool always allowed (file investigation)

3. **PreToolUse soft warning** (`warn-code-gen-routing.sh`)
   - Warns before writing code files without or-task.sh routing (Rule 20)
   - Allows write to proceed (soft gate)
   - Silent if message contains "or-task"/"deepseek"

**Configuration:** Modified `~/.claude/settings.json` to add three hook definitions under SessionStart and PreToolUse.

**State file:** `~/.claude/session-intake-state.json` (global, resets per new chat)

**How to apply if revisiting:**
- Consider lowering friction: perhaps soft warning instead of hard block on PreToolUse
- Keep SessionStart reminder (low-friction)
- Refine "skip" keyword behavior or scope
- Test again in multi-project workflow to gauge impact on productivity

**Files created (now deleted):**
- `~/.claude/hooks/enforce-intake-startup.sh`
- `~/.claude/hooks/verify-intake-done.sh`
- `~/.claude/hooks/warn-code-gen-routing.sh`

**Rollback completed:** 2026-07-20 — settings.json restored, hooks deleted, state file removed, backup cleaned up.

**Next time:** Start with soft warnings only, or explore less intrusive approaches (e.g., visual reminders in responses without blocking).
