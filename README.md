# plugins

A [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugins/create-marketplace) maintained by Kristof Degrave. Add it once, then install plugins from it by name.

## Plugins

| Plugin | Description | Version |
| :- | :- | :- |
| [`playbook`](plugins/playbook) | An opinionated development playbook for Claude Code, installed into a project and kept up to date with `/playbook:setup`. | 0.1.0 |

## Install

The `playbook` plugin depends on [`mattpocock-skills`](https://github.com/mattpocock/skills), so add that marketplace first. Run these inside a Claude Code session:

```text
/plugin marketplace add mattpocock/skills
/plugin marketplace add kristofdegrave/plugins
/plugin install playbook@plugins
```

Then run `/playbook:setup` in the project you want the playbook installed in.

## Update

Update the plugin, then rerun the setup skill. The skill is rerunnable: it detects what is already in place and applies only what changed.

```text
/plugin marketplace update plugins
/plugin update playbook@plugins
/playbook:setup
```

## Develop

Load a plugin straight from this checkout without installing it:

```bash
claude --plugin-dir plugins/playbook
```

Validate the marketplace and the plugin after every edit:

```bash
claude plugin validate .
claude plugin validate plugins/playbook
```

## License

[MIT](LICENSE)
