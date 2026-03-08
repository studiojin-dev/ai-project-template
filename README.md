# AI Project Template

This repository is a reusable instruction template for coding AI tools.
It keeps repository rules tool-neutral while still supporting tool-specific entry files and an optional Codex global setup.

## File Map

- `AGENTS.md`: canonical repository rules shared across tools
- `CODEX.md`: Codex entry file that points back to `AGENTS.md`
- `CLAUDE.md`: Claude entry file that points back to `AGENTS.md`
- `GEMINI.md`: Gemini entry file that points back to `AGENTS.md`
- `CODEX_GLOBAL_AGENTS.md`: optional Codex global template for `~/.codex/AGENTS.md`
- `skills/*`: shared specialist review lanes to install into each tool's skills directory
- `.claude/agents/*`: optional Claude specialist agents aligned with the shared review lanes

## Usage Model

Use the files in two separate ways:

1. Repository-local setup
   Copy `AGENTS.md` and the tool entry files you need into another repository.
   If you want the specialist review lanes described by this template, also
   install the bundled `skills/` directory into the matching tool's skills
   directory. For Claude, you can also install the bundled `.claude/agents/`.

2. Optional Codex global setup
   Copy `CODEX_GLOBAL_AGENTS.md` to `~/.codex/AGENTS.md` if you want stronger
   Codex orchestration defaults across all repositories.
   Install the bundled `skills/` into `~/.codex/skills` at the same time.

`AGENTS.md` stays repository-specific.
`CODEX_GLOBAL_AGENTS.md` is personal Codex configuration.

## Apply To Another Repository

Run these commands from this template repository:

```bash
SOURCE_REPO="$(pwd)"
TARGET_REPO="/path/to/your-project"

cp "$SOURCE_REPO/AGENTS.md" "$TARGET_REPO/AGENTS.md"
cp "$SOURCE_REPO/CODEX.md" "$TARGET_REPO/CODEX.md"
cp "$SOURCE_REPO/CLAUDE.md" "$TARGET_REPO/CLAUDE.md"
cp "$SOURCE_REPO/GEMINI.md" "$TARGET_REPO/GEMINI.md"
```

If the target repository does not use one of those tools, omit that file.

If you also want the bundled shared skills:

```bash
mkdir -p "$TARGET_REPO/.codex/skills"
cp -R "$SOURCE_REPO/skills/." "$TARGET_REPO/.codex/skills/"

mkdir -p "$TARGET_REPO/.claude/skills"
cp -R "$SOURCE_REPO/skills/." "$TARGET_REPO/.claude/skills/"

mkdir -p "$TARGET_REPO/.gemini/skills"
cp -R "$SOURCE_REPO/skills/." "$TARGET_REPO/.gemini/skills/"
```

If you also want the bundled Claude agents:

```bash
mkdir -p "$TARGET_REPO/.claude/agents"
cp -R "$SOURCE_REPO/.claude/agents/." "$TARGET_REPO/.claude/agents/"
```

## Install Codex Global Defaults

Run this command from this template repository:

```bash
SOURCE_REPO="$(pwd)"
mkdir -p "$HOME/.codex"
cp "$SOURCE_REPO/CODEX_GLOBAL_AGENTS.md" "$HOME/.codex/AGENTS.md"
mkdir -p "$HOME/.codex/skills"
cp -R "$SOURCE_REPO/skills/." "$HOME/.codex/skills/"
```

Those copies make the checked-in Codex orchestration template active at
`~/.codex/AGENTS.md` and install the shared specialist skills alongside it.

## Install Shared Skills

If you follow this template and want the specialist lanes it references, install
the bundled `skills/` directory together with the instruction files.

### Codex global install

```bash
SOURCE_REPO="$(pwd)"
mkdir -p "$HOME/.codex/skills"
cp -R "$SOURCE_REPO/skills/." "$HOME/.codex/skills/"
```

### Claude global install

```bash
SOURCE_REPO="$(pwd)"
mkdir -p "$HOME/.claude/skills"
cp -R "$SOURCE_REPO/skills/." "$HOME/.claude/skills/"
```

### Gemini global install

```bash
SOURCE_REPO="$(pwd)"
mkdir -p "$HOME/.gemini/skills"
cp -R "$SOURCE_REPO/skills/." "$HOME/.gemini/skills/"
```

### Claude global agents install

```bash
SOURCE_REPO="$(pwd)"
mkdir -p "$HOME/.claude/agents"
cp -R "$SOURCE_REPO/.claude/agents/." "$HOME/.claude/agents/"
```

## Optional Skill Recommendation

This template does not require ADRs.
If your project later starts recording architectural decisions, I recommend also
adding [`adr-index-skill`](https://github.com/studiojin-dev/adr-index-skill)
to your tool's skills directory.

It is a lightweight skill for Codex, Claude, and Gemini that keeps ADR history
out of `AGENTS.md` and generates a small searchable index.

## Install `adr-index-skill`

Source: [studiojin-dev/adr-index-skill](https://github.com/studiojin-dev/adr-index-skill)

### Codex global install

```bash
git clone https://github.com/studiojin-dev/adr-index-skill.git \
  ~/.codex/skills/adr-index
```

Restart Codex after installation.

### Codex repository-scoped install

```bash
mkdir -p .codex/skills
git clone https://github.com/studiojin-dev/adr-index-skill.git \
  .codex/skills/adr-index
```

### Claude install

Repository-scoped:

```bash
mkdir -p .claude/skills
git clone https://github.com/studiojin-dev/adr-index-skill.git \
  .claude/skills/adr-index
```

Global:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/studiojin-dev/adr-index-skill.git \
  ~/.claude/skills/adr-index
```

### Gemini install

Repository-scoped:

```bash
mkdir -p .gemini/skills
git clone https://github.com/studiojin-dev/adr-index-skill.git \
  .gemini/skills/adr-index
```

If your Gemini environment supports a global skills directory, you can install
the same repository there as well.

After installation, invoke the skill with `$adr-index` in Codex or `/adr-index`
in Claude and Gemini.

## AI-Friendly Prompts

You can also ask a coding AI to apply the template directly.

### Repository-local setup

```text
Copy `AGENTS.md`, `CODEX.md`, `CLAUDE.md`, and `GEMINI.md` from this repository into the target repository root.
Keep `AGENTS.md` as the canonical shared rules file.
Keep the tool-specific files as lightweight entry files that direct the tool back to `AGENTS.md`.
Install the bundled `skills/` directory into the target tool's skills directory as well.
If the target tool is Claude and you want specialist agents, also copy `.claude/agents/`.
```

### Codex global setup

```text
Copy `CODEX_GLOBAL_AGENTS.md` from this repository to `~/.codex/AGENTS.md`.
If `~/.codex/AGENTS.md` already exists, replace it with the contents of `CODEX_GLOBAL_AGENTS.md`.
Confirm that the final destination path is `~/.codex/AGENTS.md`.
Install the bundled `skills/` directory into `~/.codex/skills` at the same time.
```

## Tool Notes

### Codex

- Read `AGENTS.md` first for repository behavior.
- Use `CODEX.md` as the repository entry file.
- Use `CODEX_GLOBAL_AGENTS.md` only for the optional global Codex setup.
- Install `skills/` into `.codex/skills/` or `~/.codex/skills/` if you want the
  bundled specialist review lanes.

### Claude

- Read `AGENTS.md` first.
- Use `CLAUDE.md` as the lightweight repository entry file.
- Install `skills/` into `.claude/skills/` or `~/.claude/skills/` if you want
  the bundled specialist review lanes.
- Install `.claude/agents/` into the matching Claude agents directory if you
  want Claude-specific specialist agents.

### Gemini

- Read `AGENTS.md` first.
- Use `GEMINI.md` as the lightweight repository entry file.
- Install `skills/` into `.gemini/skills/` or `~/.gemini/skills/` if you want
  the bundled specialist review lanes.
