# gh-workon

Create a git branch from a GitHub issue and assign it to yourself.

## Demo

#### Simple
https://user-images.githubusercontent.com/98980/200496618-bbd935dd-e34e-4e06-936b-d35b212a6e83.mp4

### Using worktree and selecting the branch from where to start

https://github.com/chmouel/gh-workon/assets/98980/d3fd47c2-5eab-41d1-b933-c985161a6506

## Installation

```shell
gh extension install chmouel/gh-workon
```

### Requirements

- [GH](https://github.com/cli/cli)
- GNU sed
- GNU awk
- [FZF](https://github.com/junegunn/fzf)

## Usage

gh workon extension let you choose an issue from a list of issues with FZF and
automatically create a branch out of it and assign the issue to yourself.

If you specify a query as the first argument, it will be used to filter the list of title matching this query.

```shell
gh workon "crash"
```

if you add a `-c` it will generate a commit message with the issue title and the issue number. You can automate the creation of the commit this like this :

```shell
git commit -m "$(gh workon -c)" --edit
```

The `-N` flag will not create any branch and just print the one that would have been created.

When you have the `-F` it will use the issue number directly and not try to
choose any via fzf (useful if you have a old issue reaching the gh issue list
limit)

You can specify the flag `-p` to prompt for a branch (with fzf) from where the new branch or worktree will start from.

You can specify a -w with a basedir as argument to have a worktree created in the basedir (with the issue name appended) and a new branch.

## Git hooks

If you install the script [prepare-commit-msg](./prepare-commit-msg) into your
`.git/hooks` directory (make sure it is set as executable). It will automatically
detect if you are in branch named `issue-NUMBER` and prepare a commit message out
of the issue title for you.

It tries to do the right thing and only add the `Fixes #ISSUE_NUMBER` if there is already a commit message but that `Fixes` keywork is not there.

## TODO

- Support glab
- Create worktree instead of branch
- Convert it to go/rust/python to avoid shell quoting issues.

## BUGS

- may be buggy with some characters due of shell quoting issues.

## Copyright

[Apache-2.0](./LICENSE)

## Authors

Chmouel Boudjnah

- Fediverse - <[@chmouel@chmouel.com](https://fosstodon.org/@chmouel)>
- Twitter - <[@chmouel](https://twitter.com/chmouel)>
- Blog  - <[https://blog.chmouel.com](https://blog.chmouel.com)>
