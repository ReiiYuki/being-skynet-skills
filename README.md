# being-skynet-skills

A collection of highly robust, production-grade agent skills designed to create autonomous, self-healing, and infinite-looping AI agent workflows. These skills are fully compatible with tools like `agent-skills-cli`, Claude Code, Cursor, and the Antigravity SDK.

## Available Skills

1. **[Checkpoint Manager](./checkpoint-manager/SKILL.md)**: Instills a risk-averse persona into the agent. The agent proactively creates isolated, non-git local backups in a `.checkpoints` directory before executing large multi-file refactors or risky changes, ensuring no progress is ever lost during long-running tasks.
2. **[Exhaustive Development Loop](./exhaustive-development-loop/SKILL.md)**: Instills an unrelenting developer persona. It forces the agent into a continuous `Research -> Develop -> Revalidate -> Checkpoint` loop, allowing it to autonomously iterate until the project is perfect or the token limit is physically reached.

## Installation

### Using agent-skills-cli (Recommended)

You can easily install these skills globally using the `agent-skills-cli` via npx:

```bash
# Install Checkpoint Manager
npx agent-skills add github:ReiiYuki/being-skynet-skills/checkpoint-manager

# Install Exhaustive Development Loop
npx agent-skills add github:ReiiYuki/being-skynet-skills/exhaustive-development-loop
```

### Manual Installation

Alternatively, you can clone this repository and manually copy the respective folders into your agent's local `.skills` or context directory.

## Sponsor

If you find this project helpful, please consider sponsoring me on GitHub to support further development! 💖
[Sponsor ReiiYuki on GitHub](https://github.com/sponsors/ReiiYuki)

## License

This project is licensed under the [MIT License](./LICENSE).
