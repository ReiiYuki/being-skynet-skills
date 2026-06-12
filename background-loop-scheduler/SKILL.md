---
name: background-loop-scheduler
description: Schedules automated tasks right before token limits are exceeded or when rate limits are hit. It calculates the necessary delay, checkpoints work, and schedules a fresh session to continue infinite loops.
---

# Background Loop Scheduler

## Overview

Enable infinite autonomy by intelligently managing context windows and API rate limits. Instead of failing when you run out of tokens or hitting a quota wall, you will preemptively checkpoint your state, calculate the time required for tokens to refill (or for a fresh session to spin up), and schedule an automated task to wake yourself up and continue working.

## When to Use

- You sense your **context window (token limit)** is getting full due to a very long conversation history.
- You encounter an **API Rate Limit** or "Quota Exceeded" error (e.g., Tokens Per Minute exhausted).
- The `exhaustive-development-loop` needs to safely restart in a fresh session to clear memory bloat.

**When NOT to use:** If the task is simple and you have plenty of context window and API quota remaining.

## The Intelligent Scheduling Process

### Step 1: Monitor Token Usage
Constantly be aware of two limitations:
1. **Context Window:** The total number of tokens in your current conversation.
2. **Rate Limits:** The speed at which you are consuming API quota.

### Step 2: Calculate Schedule Delay
If you are approaching a limit, determine the optimal sleep duration:
- **For Context Window Refresh:** If your memory is just bloated, you only need a short delay (e.g., `60 seconds`) to spin down the current heavy session and schedule a fresh, empty session to pick up the task.
- **For API Rate Limits:** If you hit a hard quota (like a daily or minute limit), read the error message or estimate the refill time. Set the delay precisely to match the time when tokens will refill (e.g., `3600 seconds`).

### Step 3: Secure the State (Checkpoint)
- **CRITICAL:** You must invoke the `checkpoint-manager` skill immediately.
- Do not let the session die without saving. Log exactly what was accomplished and what the next session must do in `CHECKPOINTS_LOG.md`.

### Step 4: Create the Scheduled Task
Use your built-in `schedule` tool (e.g., `DurationSeconds` for a one-shot timer).
- Set the duration calculated in Step 2.
- **Prompt definition:** Set a highly specific prompt so the awakened agent knows exactly where to resume.
  *Example Prompt:* `"Wake up. Your previous session hit a token limit. Context has been cleared. Read CHECKPOINTS_LOG.md to retrieve your state, and instantly resume the exhaustive-development-loop from where you left off."`

### Step 5: Terminate Current Session
Once the schedule is successfully registered, cleanly exit your turn. The system will handle the automated resurrection at the scheduled time, ensuring a truly infinite workflow.
