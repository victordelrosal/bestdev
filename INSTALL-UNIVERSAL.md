# COMPASS Universal Installation Guide

**Install COMPASS across all major AI coding assistants**

This guide shows you how to install COMPASS-MINI.md as your coding standard across GitHub Copilot, Cursor, Windsurf, Aider, Continue.dev, and Claude Code.

---

## What is COMPASS?

**COMPASS anchors AI in the engineering discipline human developers already trust.**

It draws from battle-tested standards:
- **OWASP** for secure-by-default design
- **SOLID** for architecture
- **Test-Driven Development** for reliability
- **YAGNI** for simplicity
- **Defensive programming** for robustness
- **Systematic debugging protocols** for problem-solving

COMPASS is the accumulated wisdom of modern software engineering in one framework—giving AI assistants the same foundation that professional developers rely on.

**One source of truth:** COMPASS-MINI.md
**Deployment:** Via each tool's native configuration format

---

## Quick Overview

| AI Tool | Best Method | File Location | Talk-to-AI Approach |
|---------|-------------|---------------|---------------------|
| **Claude Code** | SessionStart hook | `~/.claude/settings.json` | ✅ Easiest |
| **Cursor** | Rules file | `.cursor/rules/*.mdc` | ✅ Easy |
| **GitHub Copilot** | Instructions file | `.github/copilot-instructions.md` | ⚠️ Manual setup |
| **Windsurf** | Rules file | `.windsurfrules` | ✅ Easy |
| **Aider** | Config + read | `.aider.conf.yml` | ⚠️ Manual setup |
| **Continue.dev** | Config rules | `~/.continue/config.yaml` | ⚠️ Manual setup |

---

## Tool-Specific Installation

Each AI tool reads COMPASS-MINI.md via its native configuration format:

---

### 1. Claude Code

**The "Just Talk" Approach** ✅

Start Claude Code and say:

```
I want to install COMPASS so it loads automatically in every Claude Code session.

The COMPASS-MINI.md file is located at: /path/to/COMPASS-MINI.md

Please:
1. Update my global ~/.claude/settings.json to add a SessionStart hook
2. Create a /compass command to refresh it during sessions
```

Claude Code will handle everything automatically.

**Manual Setup** (for reference):

1. Edit `~/.claude/settings.json`
2. Add this configuration:

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "cat /absolute/path/to/COMPASS-MINI.md"
          }
        ]
      }
    ]
  }
}
```

**Context Limit:** No explicit limit
**Docs:** https://code.claude.com/docs/en/hooks

---

### 2. Cursor

**The "Just Talk" Approach** ✅

In Cursor, say:

```
I want to add COMPASS-MINI.md as persistent coding rules.

The file is at: /path/to/COMPASS-MINI.md

Please create .cursor/rules/compass.mdc with the COMPASS content.
```

**Manual Setup - Option A: .cursor/rules (Recommended)**

1. Create `.cursor/rules/compass.mdc`
2. Add frontmatter and COMPASS content:

```yaml
---
description: "COMPASS coding standards"
alwaysApply: true
---

[Paste COMPASS-MINI.md content here]
```

**Manual Setup - Option B: UI**

1. Open Cursor Settings
2. Go to "Rules" → "Project Rules"
3. Click "Edit in .cursorrules"
4. Paste COMPASS content

**Context Limit:** <500 lines per rule (COMPASS-MINI.md fits)
**Docs:** https://cursor.com/docs/context/rules

---

### 3. GitHub Copilot

**Manual Setup Required** ⚠️

1. Create `.github/` directory in project root
2. Create `.github/copilot-instructions.md`
3. Paste COMPASS-MINI.md content (condense to ~2 pages if needed)
4. Enable in IDE:
   - **VS Code:** Settings → GitHub → Copilot → Copilot Chat → Enable "custom instructions"
   - **Visual Studio:** Tools → Options → GitHub → Copilot → Copilot Chat → Enable checkbox

**For path-specific rules:**

Create `.github/instructions/backend.instructions.md`:

```yaml
---
applyTo: "backend/**/*.py"
---

[Python-specific COMPASS rules]
```

**Context Limit:** ~2 pages / 64K tokens
**Docs:** https://docs.github.com/en/copilot/how-tos/configure-custom-instructions

---

### 4. Windsurf

**The "Just Talk" Approach** ✅

In Windsurf, say:

```
I want to add COMPASS-MINI.md as workspace AI rules.

The file is at: /path/to/COMPASS-MINI.md

Please create .windsurfrules with the COMPASS content formatted as a numbered list.
```

**Manual Setup - Option A: File**

1. Create `.windsurfrules` in project root
2. Paste COMPASS content (format as bulleted/numbered lists preferred)

**Manual Setup - Option B: UI**

1. Open Settings → Set Workspace AI Rules
2. Click "Edit Rules"
3. Paste COMPASS content

**For global rules (all projects):**

1. Click Customizations icon in Cascade menu
2. Configure `global_rules.md`

**Context Limit:** 6K characters per file, 12K total (global + workspace)
**Docs:** https://docs.windsurf.com/windsurf/cascade/memories

---

### 5. Aider

**Manual Setup Required** ⚠️

1. Create `.aider.conf.yml` in project root (or `~/.aider.conf.yml` for global)
2. Add this configuration:

```yaml
# Read COMPASS as persistent context
read: COMPASS-MINI.md

# Optional: Model configuration
model: claude-3-5-sonnet-20241022

# Optional: Auto-commit changes
auto-commits: true
git: true
```

3. Ensure `COMPASS-MINI.md` is in the same directory

**For multiple context files:**

```yaml
read:
  - COMPASS-MINI.md
  - docs/ARCHITECTURE.md
  - CONVENTIONS.md
```

**Context Limit:** No explicit limit (managed via `map-tokens` setting)
**Docs:** https://aider.chat/docs/config/aider_conf.html

---

### 6. Continue.dev

**Manual Setup Required** ⚠️

1. Open Continue Chat (`Cmd/Ctrl + L` in VS Code)
2. Click Agent selector → Gear icon → "Open configuration file"
3. **OR** find config at:
   - **Mac/Linux:** `~/.continue/config.yaml`
   - **Windows:** `%USERPROFILE%\.continue\config.yaml`

4. Add rules section with condensed COMPASS principles:

```yaml
name: MyProject
version: 0.0.1
schema: v1

models:
  - uses: anthropic/claude-3.5-sonnet
    with:
      ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}

# COMPASS rules (condensed for Continue.dev)
rules:
  - "ALWAYS validate ALL inputs with allowlist validation"
  - "ALWAYS use parameterized queries/prepared statements"
  - "NEVER concatenate user input into queries or commands"
  - "ALWAYS use proven auth libraries (never roll your own)"
  - "ALWAYS verify authorization for protected operations"
  - "NEVER commit secrets to version control"
  - "Follow TDD: Write failing test, confirm failure, write code, confirm success"
  - "Minimum 70% test coverage required"
  - "Make SMALLEST reasonable change - match existing patterns"
  - "NEVER rewrite without explicit permission"
  - "STOP and ASK when data operations might cause loss"
  - "STOP and ASK when multiple valid approaches exist"
```

**Note:** Continue.dev works best with concise bullet points rather than the full COMPASS document.

**Context Limit:** Model-dependent
**Docs:** https://docs.continue.dev/customize/deep-dives/configuration

---

## Recommended Installation Strategy

### For Individual Projects

**Best approach:**

1. **Place COMPASS-MINI.md in project root** as reference
2. **Configure each tool** you use with tool-native format
3. **Version control** all instruction files

**Example project structure:**

```
your-project/
├── COMPASS-MINI.md                    # Source reference
├── .github/
│   └── copilot-instructions.md        # GitHub Copilot
├── .cursor/
│   └── rules/
│       └── compass.mdc                # Cursor
├── .windsurfrules                     # Windsurf
└── .aider.conf.yml                    # Aider
```

### For Global Settings (All Projects)

**Tools that support global config:**

1. **Claude Code:** `~/.claude/settings.json` (SessionStart hook reads COMPASS-MINI.md)
2. **Continue.dev:** `~/.continue/config.yaml` (rules array with COMPASS principles)
3. **Aider:** `~/.aider.conf.yml` (read parameter pointing to global COMPASS location)
4. **Windsurf:** Global rules via UI

**GitHub Copilot and Cursor:** Project-specific only

---

## Context Limits Summary

When adapting COMPASS for different tools:

| Tool | Limit | Recommendation |
|------|-------|----------------|
| GitHub Copilot | ~2 pages / 64K tokens | Condense COMPASS to key principles |
| Cursor | <500 lines per rule | Full COMPASS-MINI.md fits |
| Windsurf | 6K chars/file, 12K total | Condense or split into 2 files |
| Aider | No hard limit | Full COMPASS-MINI.md works |
| Continue.dev | Model-dependent | Convert to concise bullet points |
| Claude Code | No hard limit | Full COMPASS-MINI.md works |

---

## Condensing COMPASS for Small Limits

If your tool has strict context limits, create a condensed version focusing on:

### Critical Rules Only (Fits most limits)

```markdown
# COMPASS Core Rules

## Security (NON-NEGOTIABLE)
- ✅ ALWAYS validate inputs with allowlists
- ✅ ALWAYS use parameterized queries
- ❌ NEVER concatenate user input into queries/commands
- ❌ NEVER commit secrets to version control
- ✅ ALWAYS encrypt sensitive data

## Data Safety (CRITICAL)
- STOP and ASK before any data modification
- Back up data before schema changes
- Make ONE change at a time
- Have specific rollback plan

## Testing (REQUIRED)
- Write failing test first
- Confirm failure before coding
- Write ONLY enough code to pass
- Minimum 70% coverage
- Test output must be pristine

## Development Standards
- Make SMALLEST reasonable change
- Match existing code patterns
- NEVER rewrite without permission
- NEVER add unrequested features (YAGNI)
- Commit frequently with clear messages

## When to STOP and ASK
- Data operations might cause loss
- Multiple valid approaches exist
- Security implications unclear
- Unfamiliar code/patterns
```

---

## What to Tell Users

### Simple Version (Just Talk to AI)

**"Want to install COMPASS? Here's what to say to your AI coding assistant:"**

**For Claude Code, Cursor, or Windsurf:**
```
I want to add COMPASS coding standards that load automatically.

The COMPASS-MINI.md file is at: /path/to/COMPASS-MINI.md

Please set it up so it loads in every session.
```

**For other tools:** Share this guide and point them to their tool's section.

---

### Complete Version

**"Installing COMPASS across all your AI tools:"**

1. **Clone/download COMPASS repository**
2. **Choose your approach:**
   - **Tool-specific:** Follow instructions for each tool you use
   - **Global:** Configure once for all projects (Claude Code, Aider, Continue.dev, Windsurf)
   - **Both:** Project-specific for some tools, global for others

3. **Talk to your AI** (Claude Code, Cursor, Windsurf) for easiest setup
4. **Manual config** for GitHub Copilot, Aider, Continue.dev

---

## Verifying Installation

### Test with a simple request:

In your AI coding assistant, ask:

```
What are the COMPASS security requirements for handling user input?
```

**Expected response should reference:**
- Allowlist validation
- Parameterized queries
- Never concatenating user input
- Never trusting client-side validation

If the AI doesn't reference COMPASS rules, the installation may not be working.

---

## Troubleshooting

### COMPASS not loading

**Check:**
1. File path is absolute and correct
2. File exists and is readable
3. Config file syntax is valid (JSON/YAML)
4. Tool-specific settings are enabled (GitHub Copilot, Cursor)
5. Try restarting the IDE/tool

### Context limit exceeded

**Solutions:**
1. Use the condensed COMPASS version (see above)
2. Split rules across multiple files (if tool supports)
3. Keep only critical rules (P0 priority items)

### AI ignoring COMPASS rules

**Check:**
1. Rules are loading (verify installation)
2. Be explicit in requests: "Following COMPASS standards, implement X"
3. Some tools may deprioritize rules under token pressure

---

## Updating COMPASS

When COMPASS-MINI.md is updated:

**Tools with file references (auto-update):**
- ✅ Claude Code (reads fresh each session)
- ✅ Aider (reads on each run)

**Tools with embedded content (manual update):**
- ⚠️ GitHub Copilot: Update `.github/copilot-instructions.md`
- ⚠️ Cursor: Update `.cursor/rules/*.mdc`
- ⚠️ Windsurf: Update `.windsurfrules`
- ⚠️ Continue.dev: Update `~/.continue/config.yaml` rules

**Pro tip:** Create a sync script to copy COMPASS-MINI.md to all config locations.

---

## Advanced: Automated Sync Script

Create `sync-compass.sh` to update all tools:

```bash
#!/bin/bash

COMPASS_PATH="/path/to/COMPASS-MINI.md"

# Update GitHub Copilot
if [ -d ".github" ]; then
    cp "$COMPASS_PATH" ".github/copilot-instructions.md"
    echo "✅ Updated GitHub Copilot instructions"
fi

# Update Cursor
if [ -d ".cursor/rules" ]; then
    cat > ".cursor/rules/compass.mdc" << 'EOF'
---
description: "COMPASS coding standards"
alwaysApply: true
---

EOF
    cat "$COMPASS_PATH" >> ".cursor/rules/compass.mdc"
    echo "✅ Updated Cursor rules"
fi

# Update Windsurf
if [ -f ".windsurfrules" ]; then
    cp "$COMPASS_PATH" ".windsurfrules"
    echo "✅ Updated Windsurf rules"
fi

echo "🎉 COMPASS synced across all tools!"
```

Run after updating COMPASS-MINI.md:
```bash
chmod +x sync-compass.sh
./sync-compass.sh
```

---

## Resources

- **COMPASS Repository:** [Your repo URL]
- **Tool-specific docs:** See each tool's section above
- **Community examples:**
  - GitHub Copilot: https://github.com/github/awesome-copilot
  - Cursor: https://cursor.directory/
  - Windsurf: https://windsurf.com/editor/directory

---

## Summary

**COMPASS is your single source of truth** - battle-tested engineering principles for AI assistants.

**Installation approaches:**

1. **Talk to AI** (easiest for Claude Code, Cursor, Windsurf)
2. **Manual config** (GitHub Copilot, Aider, Continue.dev need setup)
3. **Global settings** (Claude Code, Continue.dev, Aider, Windsurf support cross-project config)

**Key principle:**
- **One source:** COMPASS-MINI.md
- **Multiple deployments:** Each tool's native format
- **Consistent standards:** Same engineering discipline across all AI tools

Choose the installation method that fits your workflow and the tools your team uses!
