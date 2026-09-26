# workspace-template

Toha template for my personal workspaces.

```sh
toha apply --trust <path-or-git-url> ./<workspace-slug>
```

`--trust` lets the hooks clone the workspace branch of the kanban,
mnemonic-vault, and workflows repositories. When a branch does not exist, the
hook creates it as an orphan branch and pushes it.
