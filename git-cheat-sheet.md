# Git Cheat Sheet

Get available Git commands.
```
$ git help
```

## Configuration (https://git-scm.com/docs/git-config)

Add ```--global``` flag to ```config``` command to set global configuration (```~/.gitconfig```) or omit it to set local configuration (```[project]/.git/config```). This is helpful if you are using multiple git host services and/or email addresses.

Set the name you want attached to your commit transactions.
```
$ git config --global user.name "John Doe"
```

Set the email you want attached to your commit transactions.
```
$ git config --global user.email johndoe@example.com
```

Set the default text editor. If not configured, Git uses your system’s default editor.
```
$ git config --global core.editor vi
```

Set colorization of command line output.
```
$ git config --global color.ui auto
```

List all the settings Git can find.
```
$ git config --list
```

Get a specific key’s value.
```
$ git config user.name
```

## Repositories

Create a new local repository. (https://git-scm.com/docs/git-init)
```
$ git init
```

Download a project and its version history. (https://git-scm.com/docs/git-clone)
```
$ git clone [url]
```

## Branches (https://git-scm.com/docs/git-branch)

List all local branches in the current repository.
```
$ git branch
```

Create a new branch.
```
$ git branch [branch-name]
```

Switch to the specified branch.
```
$ git checkout [branch-name]
```

Merge the specified branch in to the current branch.
```
$ git merge [branch-name]
```

Delete the specified branch.
```
$ git branch -D [branch-name]
```

## References

* [Pro Git](https://git-scm.com/book/en/v2)
* [GitHub Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet/)
