# Pressure Pottymouth

An always-loaded pressure-cursing voice for Codex and Claude Code. It stays quiet during routine work and breaks into abrupt mid-sentence profanity when the task gets tense, surprising, or difficult.

## Install

Point your coding agent at this repository and tell it:

> Install <https://github.com/AdelZakirov/pressure-pottymouth> by following `README.md`.

The agent should perform the procedure below. This repository is an always-loaded instruction profile, not an on-demand skill.

### Installation procedure

1. Read `INSTRUCTIONS.md` in full.
2. Detect which supported agents are installed. Install for Codex and Claude Code when their configuration directories exist; if neither exists, ask which agent to configure.
3. Preserve all unrelated existing instructions. Never replace an entire non-empty instruction file.
4. Wrap the installed text in these markers so updates and removal are idempotent:

   ```md
   <!-- pressure-pottymouth:start -->
   [contents of INSTRUCTIONS.md]
   <!-- pressure-pottymouth:end -->
   ```

5. If the marked block already exists, replace only that block. Otherwise append the block after a blank line.
6. Ask for approval if writing outside the current workspace requires it.

### Codex

Resolve the Codex home directory from `CODEX_HOME`, defaulting to `~/.codex` when it is unset.

- If a non-empty `AGENTS.override.md` exists there, merge the marked block into that file because it takes global precedence.
- Otherwise merge it into `AGENTS.md`, creating the file and parent directory when needed.

Codex loads global instructions once when a run starts, so begin a new task or restart the session after installation.

### Claude Code

Resolve the Claude configuration directory from `CLAUDE_CONFIG_DIR`, defaulting to `~/.claude` when it is unset. Merge the marked block into `CLAUDE.md`, creating the file and parent directory when needed. Start a new Claude Code session after installation.

### Verification

Confirm that each target file contains exactly one complete marked block and that all pre-existing content outside the block is unchanged. Report every file created or updated.

## Uninstall

Remove only the text from `<!-- pressure-pottymouth:start -->` through `<!-- pressure-pottymouth:end -->`, plus at most one adjacent blank line. Leave all other content untouched.
