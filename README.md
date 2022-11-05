# Support for git "colon-paths" to `cd` command

Paths supplied to git that start with `:/` are understood to be relative to
the root of the git repository.

This file adds support for such paths to the `cd` command.

## Usage

Source the file `git-colon-path-support.bash` at BASH startup.

### `cd` command

Inside a git repo
```
cd :           # go to root of repo
cd :/a/b/c     # go to ${repo_root}/a/b/c
```
and if the path doesn't start with a colon `builtin cd` is used.

### Autocomplete

When inside a git repo and the current word starts with a colon, completion will
suggest directories relative to the root of the current git repo.  Otherwise
regular completion for `cd` is performed.

#### Autocomplete limitations

Color and visible-stats will not be applied to completion candidates when
completing "colon paths".

## Future

Having had this for a few days, I'm starting to like it a lot and I wish I
could do `vim :/<something>`.  I'm going to generalize this completion
stuff so that it can easily be used for other programs like vim.

Also, although git understands "colon paths", the autocomplete for git does not.
I'm going to see if I can add my thing to git's autocomplete.
