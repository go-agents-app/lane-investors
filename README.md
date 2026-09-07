# Gabriel Operator — list-builder skill pack

Canonical skill scaffold for **Git-backed personal data lists**: `assets/list.json`, `data/records.json`, validation scripts, and authoring guides.

Published from **[go-code-bot/list-builder](https://github.com/go-code-bot/list-builder)**.

## Install

```bash
npx github:go-code-bot/list-builder
npx github:go-code-bot/list-builder add ./my-list
npx github:go-code-bot/list-builder sync ./my-list
```

Or:

```bash
curl -fsSL https://raw.githubusercontent.com/go-code-bot/list-builder/main/install.sh | bash
curl -fsSL https://raw.githubusercontent.com/go-code-bot/list-builder/main/install.sh | bash -s -- ./my-list
```

## What gets installed

```text
SKILL.md
gabriel.workspace.json
assets/list.json
references/list-contract.json
data/records.json
scripts/validate-list.js
scripts/validate-records.js
prompts/codex.md
prompts/claude-code.md
```

`assets/list.json` is the canonical portable schema-v2 definition. It stores a
stable `resourceKey`, name, description, reciprocal `pipelineRef`, and column schema.
It must not store environment-local list, collection, pipeline, or user IDs.

`gabriel.workspace.json` requires definition validation and runs records validation only
when `data/records.json` exists. Portable repositories normally omit runtime records.

In a Persona workspace, commit and push this child first. Parent publish verifies its
canonical origin and declared-branch reachability. Unmarked legacy repos use a prominent
fallback warning; marked repos require their scripts. Parent `prune` removes only stale Git
metadata and preserves the checkout. The registry has exactly one shared List.

## Validate

```bash
node scripts/validate-list.js assets/list.json
node scripts/validate-records.js data/records.json
```
