# Recursive Language Model (RLM) Skill

> **"Context is an external resource, not a local variable."**

This skill equips Claude Code (and compatible agents) with the **Recursive Language Model (RLM)** pattern described in the research paper:
**[Recursive Language Modeling (ArXiv:2512.24601)](https://arxiv.org/pdf/2512.24601)**.

It enables the agent to handle massive codebases (100+ files, millions of lines) by treating the filesystem as a database and using parallel background agents to process information recursively, eliminating "context rot".

## 📦 Installation

### For Claude Code
Run this command in your terminal:

```bash
mkdir -p ~/.claude/skills/rlm && curl -o ~/.claude/skills/rlm/SKILL.md https://raw.githubusercontent.com/Bowtiedswan/rlm-skill/main/SKILL.md
```

### For OpenCode / Other Agents
Place the `SKILL.md` file in your agent's skills directory.

## 🚀 Usage

Once installed, simply ask Claude to handle a large task:

> "Use RLM to analyze the entire codebase for security vulnerabilities."
> "Scan all 500 files and find where UserID is defined."

The skill triggers automatically on keywords like:
- "analyze codebase"
- "scan all files"
- "large repository"
- "RLM"

## 🧠 How It Works

1.  **Index**: The agent scans your file structure using `find` or `ls`.
2.  **Filter**: It uses `grep` / `ripgrep` to narrow down candidate files (Zero-Shot Filtering).
3.  **Map**: It spawns multiple **parallel background agents**. Each sub-agent reads *one* file and answers *one* question.
4.  **Reduce**: The main agent collects the structured outputs and synthesizes the final answer.

## 📜 Credits

- **Research Paper**: [Recursive Language Modeling](https://arxiv.org/pdf/2512.24601)
- **Skill Author**: [Bowtiedswan](https://x.com/Bowtiedswan)
