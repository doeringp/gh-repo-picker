# gh-repo-picker

This GitHub CLI (`gh`) extension helps you to interactively find and pick one of your GitHub repositories.
With *your* repositories, I mean repositories you own at GitHub or have been given access to.
After you have selected a repository, the name is printed to `stdout`, so you can use it in scripts or pipe it to other commands.

The extension uses the [fzf command-line fuzzy finder](https://github.com/junegunn/fzf) as UI to interactively search and select a repository.
The [search syntax](https://junegunn.github.io/fzf/search-syntax/) of `fzf`, gives you a powerful way to find the repository you want with a few keystrokes.

![Demo](https://github.com/user-attachments/assets/965a616d-0d2a-4352-8e2e-b6cada424b80)

## Prerequisites

1. [GitHub CLI](https://cli.github.com) (`gh`) - minimum version (2.0.0)

2. `fzf` (Installation instructions [here](https://junegunn.github.io/fzf/installation/))

## Install the extension

```sh
gh extension install https://github.com/doeringp/gh-repo-picker
```

## Usage

To list all you GitHub repositories you have access to:

```sh
gh repo-picker
```

## Examples

The following examples show how to use the `gh repo-picker` extension in combination with other `gh` commands.

### Clone a repository

```sh
gh repo clone $(gh repo-picker)
```

### Open the repository in the browser

```sh
gh browse --repo $(gh repo-picker)
```

### Aliases

The GitHub CLI supports [aliases](https://cli.github.com/manual/gh_alias_set) for custom commands. Create aliases for repository actions you use frequently to save time.

For example, create aliases for the commands above:

```sh
# Clone one of your repositories
gh alias set --shell clone 'gh repo clone $(gh repo-picker)'

# Open one of your repositories in the web browser
gh alias set --shell open 'gh browse --repo $(gh repo-picker) $@'

# Now you can use the aliases like this:
gh clone
gh open
gh open --settings # to jump directly to the settings page of the selected repository
```

### GitHub Enterprise Server

The GitHub CLI supports GitHub Enterprise Server.
However the `gh repo-picker` command lists only your repositories from github.com by default. To use a GitHub Enterprise Server instance instead, set the `GH_HOST` environment variable:

```sh
export GH_HOST=<hostname>
gh repo-picker
```

> [!NOTE]
> Make sure you have authenticated to the GitHub Enterprise Server instance with `gh auth login --hostname <hostname>` before.
