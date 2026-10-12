# plugins

A plugin marketplace maintained by Kristof Degrave, for [Claude Code](https://code.claude.com/docs/en/plugins/create-marketplace) and [GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/plugins-marketplace). Add it once, then install plugins from it by name.

## Plugins

| Plugin | Description | Version |
| :- | :- | :- |
| [`playbook`](plugins/playbook) | An opinionated development playbook for Claude Code, installed into a project and kept up to date with `/playbook:setup`. | 0.1.0 |

## Install

### Claude Code

The `playbook` plugin depends on [`mattpocock-skills`](https://github.com/mattpocock/skills), so add that marketplace first. Run these inside a Claude Code session:

```text
/plugin marketplace add mattpocock/skills
/plugin marketplace add kristofdegrave/plugins
/plugin install playbook@plugins
```

Then run `/playbook:setup` in the project you want the playbook installed in.

### Copilot CLI

Copilot CLI reads the same `.claude-plugin/marketplace.json` and `.claude-plugin/plugin.json` files this repo already ships for Claude Code, so there is no separate Copilot manifest. Run these in a shell:

```bash
copilot plugin marketplace add kristofdegrave/plugins
copilot plugin install playbook@plugins
```

Copilot CLI has no plugin dependencies, so the `dependencies` entry in the `playbook` manifest is ignored there. Install `mattpocock-skills` by hand, before or after `playbook`:

```bash
copilot plugin marketplace add mattpocock/skills
copilot plugin install mattpocock-skills@mattpocock
```

To remove it all again:

```bash
copilot plugin uninstall playbook
copilot plugin marketplace remove plugins
```

## Update

Update the plugin, then rerun the setup skill. The skill is rerunnable: it detects what is already in place and applies only what changed.

In Claude Code:

```text
/plugin marketplace update plugins
/plugin update playbook@plugins
/playbook:setup
```

In Copilot CLI:

```bash
copilot plugin marketplace update plugins
copilot plugin update playbook
```

## Compatibility

Both tools read the same manifests and plugin directories, but they do not support the same components in the same places:

| Component | Claude Code | Copilot CLI |
| :- | :- | :- |
| Skills in `skills/<name>/SKILL.md` | Yes | Yes |
| Hooks in `hooks/hooks.json` | Yes | Yes |
| MCP servers in `.mcp.json` | Yes | Yes |
| Commands in `commands/` | Yes | Only if the manifest's `commands` field points at the directory |
| Agents in `agents/` | Yes, `*.md` | Only `*.agent.md` files |
| Plugin dependencies | Resolved on install | Not supported, install by hand (see above) |

Copilot CLI treats this repo's plugins as "legacy" plugins, the format it shares with Claude Code, as opposed to its newer Agent Plugins 1.0 format. Details are in the [Copilot CLI plugin reference](https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-plugin-reference).

## Develop

Load a plugin straight from this checkout without installing it:

```bash
claude --plugin-dir plugins/playbook
copilot plugin install ./plugins/playbook
```

Validate the marketplace and the plugin after every edit:

```bash
claude plugin validate .
claude plugin validate plugins/playbook
```

## License

[MIT](LICENSE)
