# plugins

A [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugins/create-marketplace) maintained by Kristof Degrave. Add it once, then install plugins from it by name.

## Plugins

| Plugin | Description | Version |
| :- | :- | :- |
| [`method`](plugins/method) | An opinionated development method for Claude Code, installed into a project with `/method:setup`. | 0.1.0 |

## Install

The `method` plugin depends on [`mattpocock-skills`](https://github.com/mattpocock/skills), so add that marketplace first. Run these inside a Claude Code session:

```text
/plugin marketplace add mattpocock/skills
/plugin marketplace add kristofdegrave/plugins
/plugin install method@plugins
```

## Develop

Load a plugin straight from this checkout without installing it:

```bash
claude --plugin-dir plugins/method
```

Validate the marketplace and the plugin after every edit:

```bash
claude plugin validate .
claude plugin validate plugins/method
```

## License

[MIT](LICENSE)
