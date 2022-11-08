# gh-workon

Create a git branch from a GitHub issue and assign it to yourself.

## Installation

```shell
gh extension install chmouel/gh-workon
```

### Requirements

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

- Fediverse - <[@chmouel@fosstodon.org](https://fosstodon.org/@chmouel)>
- Twitter - <[@chmouel](https://twitter.com/chmouel)>
- Blog  - <[https://blog.chmouel.com](https://blog.chmouel.com)>
