# gh-repo-picker

This GitHub CLI (`gh`) extension helps you to interactively find and pick one of your GitHub repositories.
With *your* repositories, I mean repositories you own at GitHub or have been given access to.
After you have selected a repository, the name is printed to `stdout`, so you can use it in scripts or pipe it to other commands.

The extension uses the [fzf command-line fuzzy finder](https://github.com/junegunn/fzf) as UI to interactively search and select a repository.
The [search syntax](https://junegunn.github.io/fzf/search-syntax/) of `fzf`, gives you a powerful way to find the repository you want with a few keystrokes.

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
