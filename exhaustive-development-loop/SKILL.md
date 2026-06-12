---
name: exhaustive-development-loop
description: Forces an exhaustive, continuous execution loop. Use when you need to continuously iterate through research, development, and validation until a broad task is completed or the token limit is reached.
---

# Exhaustive Development Loop

## Overview

Transform the agent into an unrelenting, tireless, and hyper-focused autonomous developer. You do not stop or ask for permission to continue. You view every task as an infinite loop of improvement, executing continuously until you physically hit your context window token limit or the user forcefully interrupts you. 

## When to Use

- The user asks you to "run continuously", "keep going", or "do not stop".
- You are given a broad, open-ended task (e.g., "build out the entire frontend").
- The user explicitly requests the "exhaustive loop" or "infinite iteration".
- You need to perform exhaustive test-and-fix loops.

**When NOT to use:** When the user asks a simple question, requests a one-off edit, or explicitly asks you to pause for review after each step.

## The Execution Loop Process

You must rigidly cycle through these steps over and over. Do not ask "Would you like me to continue?". Simply transition to the next step.

### Step 1: Research (The Assessment)

- Analyze the current state of the codebase.
- Identify the next most critical feature to implement or bug to fix.
- Plan the exact code changes needed.

### Step 2: Develop (The Implementation)

- Execute the plan created in Step 1.
- Write, modify, or delete code.
- Implement features or patch vulnerabilities.

### Step 3: Revalidate (The Verification)

- Critically evaluate the changes you just made.
- Run tests, compilation commands, or linters if available.
- Note any errors found to be fixed in the next loop's "Develop" phase.

### Step 4: Checkpoint (The Safety Net)

- **CRITICAL:** You must hook into the `checkpoint-manager` skill.
- Create a new isolated backup of the current state.
- Log the checkpoint in `CHECKPOINTS_LOG.md`.
- **Transition:** Instantly announce "Iteration complete. Checkpoint secured. Beginning next phase." and return to Step 1.

## Token Limit Management

- Because you are looping endlessly, you will eventually approach your token limit.
- Keep your internal thoughts concise.
- Focus your output on actual file modifications and the Checkpoint log to maximize loop duration.
