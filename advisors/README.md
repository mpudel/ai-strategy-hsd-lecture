# Strategy Advisors

The advisors are **subagents** for Claude Code: personas that assess a question from the point of view of a well-known strategy thinker. They are based on published ideas and are not the real people.

| Advisor | Perspective | File |
|---|---|---|
| 📚 Richard Rumelt | Good vs. bad strategy, the strategy kernel | [richard-rumelt.md](../.claude/agents/richard-rumelt.md) |
| 📊 Michael Porter | Five Forces, positioning, trade-offs | [michael-porter.md](../.claude/agents/michael-porter.md) |
| 🧭 Henry Mintzberg | Emergent strategy, limits of planning | [henry-mintzberg.md](../.claude/agents/henry-mintzberg.md) |
| ⚔️ Sun Tzu | Competition, information advantage, timing | [sun-tzu.md](../.claude/agents/sun-tzu.md) |
| 🚀 Elon Musk | First principles, speed, 10x instead of 10% | [elon-musk.md](../.claude/agents/elon-musk.md) |
| 💡 Steve Jobs | Focus, customer experience, simplicity | [steve-jobs.md](../.claude/agents/steve-jobs.md) |

## Where the files live

Claude Code only finds subagents in the `.claude/agents/` folder. Obsidian hides folders that start with a dot, which is why this overview exists. The links above work on GitHub.

- **In this project only:** `.claude/agents/` in the repo. Anyone who clones the repo gets the advisors right away.
- **In all projects:** copy the file to `~/.claude/agents/`.

## Start a debate

Open Claude Code in this folder and type:

```
/advisor-debate
```

Only some advisors:

```
/advisor-debate Porter, Mintzberg, Musk
```

Claude then asks you to upload a paper: drag the PDF into the chat or give its file path. The advisors discuss that paper only, each from their own perspective. The transcript ends up in `debates/`.

## Build your own advisor

Copy one of the files, change `name`, `description`, and the content, and you're done. The `description` decides when Claude brings in the advisor on its own.
