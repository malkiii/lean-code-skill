# Lean Code Skill

A skill for coding agents like Claude Code and Codex. It pushes the agent to work like a senior engineer instead of a fast, slightly sloppy junior. Every rule in it comes from a specific complaint in [Andrej Karpathy's post](https://x.com/karpathy/status/2015883857489522876) about coding with LLM agents.

## Installation

Install it with the [skills](https://skills.sh) CLI:

```
npx skills add malkiii/lean-code-skill
```

Update or remove it later with `npx skills update` and `npx skills remove`.

## The problems in the post and what the skill does

### Wrong assumptions

Karpathy says the most common category of mistake is that the model makes wrong assumptions on your behalf and runs with them without checking. He adds that models don't manage their confusion, don't seek clarifications, and don't surface inconsistencies. He also notes that things get better in plan mode, and that a lightweight inline version of it is missing.

The **Ask before assuming** rules cover this. If a request is ambiguous, or the agent would have to guess a requirement, it stops and asks before writing code. It also points out inconsistencies in the request or the codebase instead of quietly picking a side. Clear tasks don't get questions, so the check stays light and doesn't turn into a plan-approval step on every edit.

### Missing tradeoffs, no pushback, sycophancy

Karpathy lists three related habits. The models don't present tradeoffs, they don't push back when they should, and they are still a little too sycophantic.

The **Push back** rules cover this. When the approach you asked for is worse than an alternative, the agent stops before implementing. It states the concern, names the better alternative, lists the tradeoffs of both, and waits for your decision. It also doesn't flatter the request or you.

### Overcomplicated, bloated code

Karpathy says the models like to overcomplicate code and APIs, bloat abstractions, and leave dead code behind. His example is an inefficient, brittle construction spread over 1000 lines. You ask whether it could just do something simpler, it agrees right away, and it cuts the code down to 100 lines. In his words, it is up to you to ask that question.

The **Keep it lean** rules move that question to the agent. It writes the smallest diff that solves the task, adds no abstractions, config options, or generality the task doesn't need, and reuses existing code and patterns before adding new ones. It removes dead code and unused imports that its own change created. Before finishing, it asks whether a much simpler solution exists and rewrites the code if one does.

### Edits outside the task

Karpathy points out that the models still sometimes change or remove comments and code they don't like or don't sufficiently understand, as a side effect, even when it has nothing to do with the task.

The **Stay in scope** rules cover this. The agent changes only what the task requires. It never modifies or deletes comments or code unrelated to the task, including code it doesn't fully understand. The one exception is a trivial fix, such as a typo or an unused import, on a line it is already editing. Every other issue it notices is left alone.

## License

MIT. See [LICENSE](LICENSE).
