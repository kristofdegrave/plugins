---
name: setup
description: Install the playbook into the current project, or bring an already-installed project up to date after a plugin update. Rerunnable. Use when the user asks to set up, initialize, bootstrap, update, or sync the playbook in a repository.
---

# Set up or update the playbook

This skill installs the playbook into the current project: it sets up the files, conventions, and workflows the playbook relies on so that later skills can build on them.

It is safe to run more than once. Rerun it after updating the plugin to bring the project in line with the newer version:

- **First run** installs everything the playbook needs.
- **Later runs** detect what is already in place, apply only what changed since the installed version, and leave user edits alone. Nothing is overwritten without being reported.

This is a placeholder. The real installation and update steps will be added in a later release.
