# Working rules

Only Claude Code works *in* this repo; this file is the whole agreement. Terms: an **issue** scopes one unit of work, one per PR; the **bot** is the `kristofdegrave-bot` account; **fresh context** is a subagent with no memory of the implementation it reviews.

## Workflow

1. **Issue first.** Every PR starts from an issue under `kristofdegrave` with a goal and acceptance criteria. None yet: file one.
2. **Branch** `<issue-number>-<short-slug>` off an up-to-date `main`, e.g. `2-agent-rules`.
3. **Commits** are authored by the bot or carry a `Co-Authored-By` Claude line.
4. **PR by the bot.** Both accounts stay logged in (`gh auth status`); the bot token is scoped to each `gh` call via the Bash tool, never by switching accounts:

   ```bash
   GH_TOKEN=$(gh auth token --user kristofdegrave-bot) gh pr create --draft --title "..." --body "Closes #<n> ..."
   GH_TOKEN=$(gh auth token --user kristofdegrave-bot) gh pr ready <n>
   ```

5. **Fresh-context review** before `gh pr ready`. Dispatch a review subagent with no conversation history: it reads the diff and the issue, checks the acceptance criteria, and posts findings as PR comments (active account, `kristofdegrave`). Address the findings, then the bot marks the PR ready.
6. **Human merge.** `kristofdegrave` approves and merges.

## Conversation

7. **One question at a time**, each with a recommended answer.

## Plugin content

8. **Dual-platform.** Every published plugin works in both Claude Code and the Copilot plugin; the README compatibility table lists what each reads.
9. **Terse.** Skills and plugin files are short and to the point: bullets over prose, every line earns its tokens, no filler, no duplication. Each fact lives in one place.
