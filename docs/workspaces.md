# Workspaces

This is what I call the combination of a local file tree + devcontainer that service it.

```tree
├── briefings/
├── dagu/
├── forks/
├── kanban/
├── memory/
├── openobserve/
├── references/
├── t3/       
├── workspace/
├── worktrees/
├── AGENTS.md
├── CLAUDE.md
└── {workspace}.code-workspace
```

## `briefings`

All of my workspaces use Lore, a universal tool for agents to communicate better with you. They can create HTML briefings which Lore will serve, providing a nicer experience when an agent is either doing planning with you or explaining something.

## `dagu`

Every workspace can run workflows using Dagu. Each `dagu` directory is a branch of my `workflows` repository, with the following structure:

```tree
├── shared/      # A git submodule to the `main` branch, and contains sub-dags.
│   ├── bin      # Shell scripts used by the sub-dags
│   ├── lib      # Shared shell scripts used by the `bin/` scripts
│   ├── skills   # Skills to create common workflow patterns
│   └── test
├── test/        # Any test scripts for your local workflows
├── wiki/        # Documentation for local workflows
└── workflows/   # Local workflows - what actually runs
```

## `forks`

I clone all forks related to the workspace in this folder. Workflows are used to keep them synced with the upstream default branch, keep PR branches rebased, resolve review comments, etc.

## `kanban`

I use `kanban-md` locally to create tasks and run them through processes with Heddle. This is how I scope work for agents.

## `memory`

I use `mnemonic` MCP server as a ubiquitus memory system for agents. This directory store workspace-specific memories.

I depart from the normal usage documented by `mnemonic` and use one memory vault for all repos in the workspace, git ignoring any .mnemonic folder globally.

Agents store observations and ephemeral handoffs and notes using mnemonic. Anything more permanent is a doc, task, Skill, or in the AGENTS.md.

## `openobserve`

This stores OpenTelemetry data/state for the workspace, although workspace telemetry is mostly stored in a R2 bucket via S3 api to save disk space.

## `references`

This directory is used to provide reference data to agents, either as part of planning, to serve as examples, or to troubleshoot a workspace related tool.

I shallow clone repositories, `git clone --depth 1`, when I want to reference a GitHub repository.

## `t3`

This store the T3Code server user/state data directory.

The following files are provided as `chezmois` dotfiles or via a layered bind mount:

```dotfiles
├── keybindings.json # dotfile
├── secrets # common bind mounted directory
│   └── provider-env-Y3Vyc29y-Q1VSU09SX0FQSV9LRVk.bin.tmpl # dotfile
└── settings.json # dotfile
```

## `workspace`

This folder contains the actual devcontainer workspace.

It could be a single monorepo.
It could be an umbrella folder containing multiple repositories.

## `worktrees`

This is where git worktrees for the workspace are created.

## `AGENTS.md`

This is the core context for the workspace provided to the agents. It contains workspace specific information.