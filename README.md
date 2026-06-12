# being-skynet-skills

A collection of highly robust, production-grade agent skills designed to create autonomous, self-healing, and infinite-looping AI agent workflows. These skills are fully compatible with tools like `agent-skills-cli`, Claude Code, Cursor, and the Antigravity SDK.

## Available Skills

1. **[Checkpoint Manager](./checkpoint-manager/SKILL.md)**: Instills a risk-averse persona into the agent. The agent proactively creates isolated, non-git local backups in a `.checkpoints` directory before executing large multi-file refactors or risky changes, ensuring no progress is ever lost during long-running tasks.
2. **[Exhaustive Development Loop](./exhaustive-development-loop/SKILL.md)**: Instills an unrelenting developer persona. It forces the agent into a continuous `Research -> Develop -> Revalidate -> Checkpoint` loop, allowing it to autonomously iterate until the project is perfect or the token limit is physically reached.

## Installation

You can install these skills globally into your agent configuration using `agent-skills-cli` or by copying the respective folders into your agent's `.skills` or context directory.

## Sponsor

If you find this project helpful, please consider sponsoring me on GitHub to support further development! 💖
[Sponsor ReiiYuki on GitHub](https://github.com/sponsors/ReiiYuki)

## License

MIT License

Copyright (c) 2026 ReiiYuki

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
