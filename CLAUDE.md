# Working rules

This repo publishes a plugin marketplace. Only Claude Code works *in* it, so this file is the whole working agreement. Terms: an **issue** scopes one unit of work, one issue per PR; the **bot** is the `kristofdegrave-bot` GitHub account that opens PRs; **fresh context** is a session or subagent with no memory of the implementation it reviews.

## Workflow

1. **Issue first.** Every PR starts from an issue filed under `kristofdegrave`, with a goal and acceptance criteria. No issue yet: file one, then start.
2. **Branch** `<issue-number>-<short-slug>` off an up-to-date `main`, e.g. `2-agent-rules`.
3. **Commits** are authored by `kristofdegrave-bot` or carry a `Co-Authored-By` Claude attribution line.
4. **PR by the bot.** Open the PR as a draft with the bot token scoped to that one call, no account switching:

   ```bash
   GH_TOKEN=$(gh auth token --user kristofdegrave-bot) gh pr create --draft --title "..." --body "..."
   ```

   The body contains `Closes #<n>` so merging closes the issue.
5. **Fresh-context review.** Before marking the PR ready, dispatch a review subagent with no conversation history. It reads the diff and the originating issue, checks the acceptance criteria, and posts its findings as PR comments. The context that wrote the code never reviews its own work. Address the findings, then mark the PR ready.
6. **Human merge.** `kristofdegrave` approves and merges. Never merge yourself.

## Conversation

7. **One question at a time.** Ask clarifying questions one by one, each with a recommended answer.

## Plugin content

8. **Dual-platform plugins.** Every plugin published from this repo must work for both Claude Code and the Copilot plugin. The README's compatibility table lists what each platform reads.
