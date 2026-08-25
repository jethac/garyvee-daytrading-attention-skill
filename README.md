# garyvee-daytrading-attention-skill

Agent skill that runs Gary Vaynerchuk's *Day Trading Attention* (HarperCollins, 2024) as a workflow. One `SKILL.md` tree for **Claude Code**, **Codex**, and **Grok**.

This is the 2024 operating system: the interest-graph shift (relevance = reach), the Modern Advertising Framework (cohorts with teeth → PAC → SOC → amplification → modern commercials → PCS), and the "only amplify proven winners" doctrine. Not a book summary — a procedure.

## Install

Clone once, then put the directory on each tool's skill path. Codex **skips symlinks** — copy for Codex, junction or copy for the others.

```powershell
git clone https://github.com/jethac/garyvee-daytrading-attention-skill garyvee-daytrading-attention-skill
```

| Tool | User skill path | Notes |
|---|---|---|
| Claude Code | `~/.claude/skills/garyvee-daytrading-attention-skill` | Also `.claude/skills/` in a repo |
| Codex | `~/.codex/skills/garyvee-daytrading-attention-skill` | Real directory, not a symlink. Also `.agents/skills/` in a repo, or `~/.agents/skills/` |
| Grok | `~/.grok/skills/garyvee-daytrading-attention-skill` | Also `.grok/skills/` in a repo |

PowerShell (Windows), from the clone:

```powershell
$src = (Resolve-Path .\garyvee-daytrading-attention-skill).Path
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills","$env:USERPROFILE\.codex\skills","$env:USERPROFILE\.grok\skills" | Out-Null
New-Item -ItemType Junction -Force -Path "$env:USERPROFILE\.claude\skills\garyvee-daytrading-attention-skill" -Target $src
New-Item -ItemType Junction -Force -Path "$env:USERPROFILE\.grok\skills\garyvee-daytrading-attention-skill" -Target $src
Copy-Item -Recurse -Force $src "$env:USERPROFILE\.codex\skills\garyvee-daytrading-attention-skill"
```

macOS / Linux:

```bash
src="$(pwd)/garyvee-daytrading-attention-skill"
mkdir -p ~/.claude/skills ~/.codex/skills ~/.grok/skills
ln -sfn "$src" ~/.claude/skills/garyvee-daytrading-attention-skill
ln -sfn "$src" ~/.grok/skills/garyvee-daytrading-attention-skill
rm -rf ~/.codex/skills/garyvee-daytrading-attention-skill
cp -R "$src" ~/.codex/skills/garyvee-daytrading-attention-skill
```

Restart the tool after install. Invoke `/garyvee-daytrading-attention-skill` (Claude, Grok) or `$garyvee-daytrading-attention-skill` (Codex).

## Layout

| File | Owns |
|---|---|
| `SKILL.md` | Procedure |
| `references/daytrading-attention.md` | Book frameworks |
| `references/campaign.example.md` | Empty campaign profile template |

Optional: copy the example to `references/campaign.md` for a local foundation the skill will load. That path is gitignored.

## Attribution

Frameworks from Vaynerchuk (2024). This is an operating procedure, not a reproduction of the book.
