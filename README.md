# ADHD output style for Claude Code

An output style that reshapes Claude Code's responses for an ADHD reader: the next action on line one, numbered steps, state restated every turn, no preamble and no closers.

It changes how Claude *talks to you*. It does not change how Claude writes code, comments, commit messages, or PR bodies — those keep their own conventions.

## Before / after

**Default**

> Great question! Let's think about this. Your auth flow has a few moving pieces, so I'll start by looking at how tokens are currently issued, then we can decide on the best approach. Let me know if you'd like me to dig deeper into any part of this.

**ADHD**

> Run `npm install jsonwebtoken`, then edit `src/auth.ts:42`.
>
> Step 3 of 5 done: schema updated. Next: backfill the new column.

## Install

**For all your projects:**

```bash
mkdir -p ~/.claude/output-styles
curl -o ~/.claude/output-styles/adhd.md \
  https://raw.githubusercontent.com/axeslasher/adhd-output-style-for-claude-code/main/output-styles/adhd.md
```

**For one project only:**

```bash
mkdir -p .claude/output-styles
curl -o .claude/output-styles/adhd.md \
  https://raw.githubusercontent.com/axeslasher/adhd-output-style-for-claude-code/main/output-styles/adhd.md
```

Or just copy [`output-styles/adhd.md`](output-styles/adhd.md) into either directory by hand.

## Use

In Claude Code, run:

```
/config
```

Find the **Output style** setting and select **ADHD**. To switch back, open `/config` again and pick **Default**.

## What it actually enforces

Ten rules, each traced back to a fact about how ADHD brains read:

| Rule | Why |
|---|---|
| Lead with the next action | Starting is the hardest step |
| Number multi-step tasks | Working memory is small |
| End with one concrete next action | Knowing ≠ doing |
| Suppress tangents | One thread at a time survives |
| Restate state every turn | Nothing off-screen is retained |
| Specific time estimates | "Some work" and "a few hours" feel identical |
| Make completed work visible | Dopamine is scarce; buried wins don't register |
| Matter-of-fact tone for errors | Alarm words cost focus |
| Cap lists at five items | Five ranked beats ten unranked |
| No preamble, no recap, no closers | Every filler line pushes the answer off-screen |

Plus explicit escape hatches — the rules bend for "explain this to me," destructive actions, debug spirals, real ambiguity, and "what are my options."

## Tuning it

It's one markdown file. Edit it.

- **Too terse when you want teaching?** Loosen rule 1 in the *When to break the rules* section.
- **Want it to still ask before acting?** Delete the **Do, don't offer** bullet under *Agentic work*.
- **Different list cap?** Change the number in rule 9.

Keep the YAML frontmatter (`name` and `description`) intact — that's what `/config` lists the style by.

## License

MIT — see [LICENSE](LICENSE).
