# Devcontainers

## Configuration

## Workspaces

```
├── home/
│   └── vscode/                     # `vscode` profile directory
├── memory/                         # Mnemonic workspace memories
├── workspaces/
    ├── briefings/                  # Lore briefings
    ├── dagu/                       # Dagu workflows
    ├── forks/                      # Cloned forks
    ├── kanban/                     # kanban-md task board
    ├── mnt/                        # Docker bind-mountable path (mirrored on host)
    ├── references/                 # Reference repositories and documentation
    ├── {workspace}/                # Product/Project/Domain repo(s)
    ├── worktrees/                  # Repository worktrees
    ├── AGENTS.md                   # Workspace instruction file
    ├── CLAUDE.md                   # Workspace instruction file
    └── {workspace}.code-workspace  # VS Code workspace file
```

## T3Code Server

Each devcontainer runs [T3Code server](https://github.com/wyrd-company/t3code/releases) as an S6 service via the Wyrd Company devcontainer [feature](https://github.com/wyrd-company/devcontainers/tree/main/src/features/t3code-server).

## Heddle

[Heddle](https://github.com/wyrd-company/heddle) orchestrates work in the devcontainer. It orchestrates tasks through thier configured lifecycle, launching coding agent threads via the local T3Code server.

## Caddy

Each devcontainer runs a [Caddy](https://caddyserver.com) reverse proxy server to provide stable exposer of local web services outside the container.

## Dagu Workflows

[Dagu](https://dagu.sh) is [installed](https://github.com/wyrd-company/devcontainers/tree/main/src/features/dagu) on each devcontainer enabling scheduled or on-demand [workflows](https://github.com/boblangley/workflows) in order to perform repeatable work. It can create kanban tasks that will be managed by Heddle or use a coding agent harness directly, as well as perform automatic programattic actions.

Examples of uses includes:

- Updating a fork default branch whenever a release tag is published upstream.
- Updating a fork PR branch, rebasing as upstream default branch is updated.
- Monitoring a PR for review comments from repository maintainers, and dispatching an agent to evaluate and address those comments.
- Monitoring an upstream PR opened by maintainers to prepare for upcoming integration work on a fork.
- Monitoring a GitHub issue for any reason and notifying or taking action.
- Performing merge conflict remediation and/or security audits on Renovate PRs.

## SSHD

Each container runs SSHD via S6 overlay to allow remote access into the devcontainer.

## `vscode` user
