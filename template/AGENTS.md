---
alwaysApply: true
---
<workspaces-context path="/workspaces">
```standard folders overview
workspaces/
├── {{ slug }}/{{ ' ' * (23 - (slug | length)) }}# The primary workspace for this devcontainer containing a product/domain theme
├── archive/                # Archived projects. Do not read unless instructed.
├── forks/                  # GitHub forks this workspace is maintaining
├── kanban/                 # local kanban-md board
├── memory/                 # This workspaces memory for mnemonic - used for all projects instead of per-repo stores
{% if uses_docker %}├── mnt/                    # Host-mirrored Docker mount point
{% endif %}├── references/             # Shallow-cloned repos or other material to use as reference
├── workflows/              # Dagu Workflows
└── worktrees/              # Git worktrees for the workspace
```
</workspaces-context>