---
name: checkpoint-manager
description: Creates isolated local backups before risky changes to prevent work loss. Use when modifying multiple files, starting a major refactor, or when you need a safe restore point during a long-running session.
---

# Checkpoint Manager

## Overview

Decompose risk by explicitly backing up project states locally. Good checkpointing is the difference between easily recovering from a failed refactor and losing hours of AI-generated progress. Checkpoints are strictly local directories and never use `git commit`, ensuring the user's version history remains clean.

## When to Use

- You are about to execute a major refactor.
- You are modifying 3 or more files simultaneously.
- A task feels high-risk or could break existing functionality.
- Another skill (like `exhaustive-development-loop`) explicitly requires a checkpoint.
- The user requests a "save state" or "checkpoint".

**When NOT to use:** When making trivial single-line changes, fixing typos, or modifying files that do not affect the execution state (like READMEs).

## The Checkpoint Process

### Step 1: Identify Target Scope

Before modifying files, operate in read-only mode to assess what needs backing up.
- Identify which files are critical to the current stable state.
- If the whole project is at risk, prepare to backup the entire working directory.
- Exclude `.git`, `node_modules`, `venv`, and existing `.checkpoints` directories.

### Step 2: Create Isolation Directory

Ensure checkpoints do not interfere with the active workspace.
- Create a directory named `.checkpoints/checkpoint_<timestamp>_<descriptive_name>` at the root of the project.

### Step 3: Execute Backup

- Copy all relevant files and directories identified in Step 1 into this new `.checkpoints/...` directory.

### Step 4: Log the State

Maintain a central source of truth for all checkpoints.
- Append an entry to `CHECKPOINTS_LOG.md` at the project root.
- Follow this exact format:

```markdown
## [YYYY-MM-DD HH:MM:SS] Checkpoint ID: checkpoint_<timestamp>_<name>
**Risk Assessment:** [Why the checkpoint was taken]
**Description:** [State of the project]
**Files Included:** [Brief summary]
```

## The Restoration Process

If a rollback is required, follow these steps strictly:

### Step 1: Verify Checkpoint
Consult `CHECKPOINTS_LOG.md` to identify the correct Checkpoint ID.

### Step 2: Execute Restoration
Copy the contents of `.checkpoints/<Checkpoint ID>/` back to their original locations, overwriting current files.

### Step 3: Log Restoration
Add a new entry to `CHECKPOINTS_LOG.md` documenting the rollback.
