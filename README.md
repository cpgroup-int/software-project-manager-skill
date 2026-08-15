# Software Project Manager Skill

A Codex skill for coordinating non-trivial software work: it selects the appropriate workflow for planning, implementation, testing, review, GitHub, and architecture tasks.

## Install

Run this from an environment with Codex's `skill-installer` helper available:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo cpgroup-int/software-project-manager-skill \
  --path software-project-manager
```

The skill will be available in a new Codex turn after installation.

## Contents

- `software-project-manager/SKILL.md` — the skill instructions.

## Scope

The skill is an orchestrator. It directs software work to focused skills such as planning, testing, debugging, source research, GitHub workflow, and quality review rather than duplicating them.
