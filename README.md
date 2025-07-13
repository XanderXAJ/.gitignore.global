# .gitignore.global

GitHub's global .gitignores catted into a single file for use with `git`.

## Why use a global .gitignore?

When working on projects, we standardise many things -- **but not everything**.

As a result, we don’t all use the same tools — **nor should we**.

**Diverse setups encourage productivity, creativity and accessibility.**

**But many tools generate clutter**: files that have no place in version control, which end up slowing repos, leaking secrets, or distracting colleagues.
**Clutter we're responsible for.**

**This project eases that burden.**
It combines [GitHub’s gitignore templates][gitignore] into [**a single global file**](.gitignore.global), helping you keep your commits clutter-free.

[gitignore]: https://github.com/github/gitignore

## Usage

### One-off `curl`

To grab the latest `.gitignore.global` in `*sh` shells:

```shell
curl -fsSL -o ~/.gitignore.global "https://raw.githubusercontent.com/XanderXAJ/.gitignore.global/refs/heads/main/.gitignore.global"
```

Then configure git to use it:

```shell
git config set --global core.excludesFile ~/.gitignore.global
```

To update `.gitignore.global`, **re-run** the above `curl` command, **or** add aliases to help you update:

```shell
# Shell alias
alias updateGitignoreGlobal='curl -fsSL -o ~/.gitignore.global "https://raw.githubusercontent.com/XanderXAJ/.gitignore.global/refs/heads/main/.gitignore.global"'
# Git alias
git config --global alias.updateGitignoreGlobal '! curl -fsSL -o ~/.gitignore.global "https://raw.githubusercontent.com/XanderXAJ/.gitignore.global/refs/heads/main/.gitignore.global"'
```

### Repo clone

If you prefer to use git, clone the repo via your preferred method (HTTP shown since it doesn't require auth):

```shell
git clone https://github.com/XanderXAJ/.gitignore.global.git ~/.gitignore.global
```

Then configure git to use it:

```shell
git config set --global core.excludesFile ~/.gitignore.global/.gitignore.global
```

To update `.gitignore.global`, run the following:

```shell
git -C ~/.gitignore.global pull
```

## FAQ

### How do I commit a file that is being excluded?

Run the following:

```shell
git add -f <file>
```

### Some IDE/tool files are still commitable. Why is that?

Some files are _intended_ to be committed despite appearing in an IDE/tool folder.

For example, here's part of the [VSCode gitignore](https://github.com/github/gitignore/blob/main/Global/VisualStudioCode.gitignore):

```gitignore
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
```

You can see some specific exclusions (lines beginning `!`) to the ignore rules.

These exclusions are intended by the tool in question to be committed, for example to allow for customisations or recommendations on a per-repo or per-project basis.
To understand more about them, look up the tool's documentation.
