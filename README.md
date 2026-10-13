# Lean Code Skill

A skill for coding agents like Claude Code and Codex. It pushes the agent toward the simplest solution that works: the smallest diff, no speculative abstractions, no dead code. Every rule in it comes from a specific complaint in [Andrej Karpathy's post](https://x.com/karpathy/status/2015883857489522876) about coding with LLM agents.

## Installation

Install it with the [skills](https://skills.sh) CLI:

```
npx skills add malkiii/lean-code-skill
```

Update or remove it later with `npx skills update` and `npx skills remove`.

## The problem in the post and what the skill does

Karpathy says the models like to overcomplicate code and APIs, bloat abstractions, and leave dead code behind. His example is an inefficient, brittle construction spread over 1000 lines. You ask whether it could just do something simpler, it agrees right away, and it cuts the code down to 100 lines. In his words, it is up to you to ask that question.

The rules move that question to the agent. It writes the smallest diff that solves the task, adds no abstractions, config options, or generality the task doesn't need, and reuses existing code and patterns before adding new ones. It removes dead code and unused imports that its own change created. Before finishing, it asks whether a much simpler solution exists and rewrites the code if one does.

## License

MIT. See [LICENSE](LICENSE).
