# PromptForge

**Git for Prompts — Version, Diff, Tag, and Deploy AI Prompts Like Code**

[![Buy on Gumroad](https://img.shields.io/badge/Buy-%2449-red)](https://empirelabs1.gumroad.com/l/promptforge)
[![by Empire Labs](https://img.shields.io/badge/by-Empire%20Labs-purple)](https://empirelabs.com.au)

---

## The Problem

Prompts are the most fragile part of any AI application. Change one word in a system prompt and your output quality can swing wildly. Yet most teams manage prompts the way developers managed code before version control existed:

```
❌ final_prompt_v2.txt
❌ final_prompt_v2_ACTUALLY_FINAL.txt
❌ final_prompt_v2_reviewed_final_v3.txt
❌ system_prompt_production_backup_may2026.txt
```

Sound familiar? The symptoms are:

- **You can't remember what changed** between the version that worked and the version that broke things
- **You can't roll back** when a "minor update" tanks output quality
- **You can't reproduce** a production issue because you don't know which prompt was live at the time
- **You can't collaborate** because prompts are sent as text files in Slack or email
- **You can't deploy confidently** because there's no release process for prompts — just "copy-paste and hope"

When your AI application's quality depends on prompt quality, managing prompts like disposable text files is a production risk.

---

## The Solution

PromptForge brings git-style version control to your prompts — purpose-built for AI workflows, no Git knowledge required.

```
$ pf init              # Start tracking prompts in this project
$ pf add my-agent      # Register a new prompt
$ pf update my-agent   # Save a new version
$ pf diff my-agent     # See exactly what changed
$ pf tag my-agent v2.0 # Mark a deployment-ready version
$ pf history my-agent  # Full version timeline
```

Every prompt has a complete, searchable history. Colour-coded diffs show exactly what changed between iterations. Tags let you mark versions for deployment. Export gives you JSON-ready prompts for your application code.

---

## What This Means For Developers

| Before PromptForge | After PromptForge |
|---|---|
| Managing prompts in .txt files with inconsistent naming | `pf add name --file prompt.txt` — structured, versioned |
| Manually diffing files to find what changed | `pf diff name` — colour-coded, instant |
| Can't roll back when a new prompt breaks things | `pf export name --version 3` — the old version is right there |
| Sending prompt text in Slack to share changes | Full version history in a `.promptforge/` directory — commit to git, share the whole repo |
| Deploying by copy-pasting into a config file | `pf export name --tag production` — scriptable, repeatable |
| No changelog — who changed what and why? | `pf history name` — every change logged with timestamps |

---

## How It Works

PromptForge stores prompt data in a local `.promptforge/` directory inside your project:

```
my-project/
├── .promptforge/          # Created by pf init
│   ├── prompts.db         # SQLite — all prompt versions stored here
│   └── config.json        # Repo settings
├── my-app/
├── README.md
└── ... your project files
```

**Everything is local.** No cloud. No account. No telemetry. No internet connection needed.

### Commands at a Glance

| Command | What It Does |
|---|---|
| `pf init` | Create a new prompt repository in the current directory |
| `pf add <name>` | Register a new prompt — provide a file or paste text |
| `pf update <name>` | Save a new version of an existing prompt |
| `pf show <name>` | Display a specific version of a prompt |
| `pf diff <name>` | Colour-coded diff between any two versions |
| `pf tag <name> <tag>` | Tag a version (e.g. `v1.0`, `production`, `test`) |
| `pf export <name>` | Export a prompt as JSON — ready for your app |
| `pf import` | Bulk import prompts from a JSON file |
| `pf history <name>` | Full version timeline for a prompt |
| `pf list` | List all tracked prompts in the repo |

### Example Workflow

```bash
# 1. Start tracking
cd my-ai-project
pf init

# 2. Add your first prompt
pf add assistant --file system-prompt.txt

# 3. Iterate — change the prompt, save a new version
pf update assistant --file system-prompt-v2.txt

# 4. See what changed
pf diff assistant

# Output (colour-coded):
# - You are a helpful assistant.
# + You are a helpful assistant. Respond concisely.
# + Cite sources when possible.

# 5. Tag for deployment
pf tag assistant production

# 6. Export into your app
pf export assistant --tag production > assistant-prompt.json
```

---

## Use Cases

### Solo Developer
Track prompt iterations across a project. Never lose a good version again. Tag `v1.0` when you deploy, iterate safely, roll back if needed. No more "which version was I using last week?"

### Team Collaboration
Add `.promptforge/` to your git repo. Everyone on your team sees the same prompt history. Pull requests now include prompt changes alongside code changes.

### CI/CD Pipeline
Export prompts to JSON during deployment. Every release is reproducible because every prompt version is traceable:

```yaml
# GitHub Actions — deploy prompts alongside code
- run: pip install promptforge
- run: pf export assistant --tag production > assistant.json
- run: deploy-ai-app assistant.json
```

### A/B Testing
Create multiple prompt versions, tag them (`control`, `variant-a`), export both, and feed them into separate model instances. Compare results side-by-side.

---

## What You Get With Purchase

- The complete PromptForge CLI (one `pip install`, zero external dependencies)
- Full documentation with workflow examples
- Prompt repository templates for common AI patterns
- 60 days of email support

---

## Requirements

- Python 3.9 or later
- That's it — no external libraries, no cloud services, no API keys

---

[**→ Purchase PromptForge on Gumroad ($49 one-time)**](https://empirelabs1.gumroad.com/l/promptforge)

*Built by [Empire Labs](mailto:contact@empirelabs.com.au)*
