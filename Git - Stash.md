# Git commands for stash
Here is an example of how to properly use  stash

| Step | Command |
| - | - |
| Create a new stash with a specific name (including tracked and untracked changes) | `git stash push -u -m "stash name"` |
| Show list of stashes and their indices | `git stash list` |
| Apply last stash | `git stash apply` |
| Apply specific stash | `git stash apply stash@{2}` |
| Delete all stashes | `git stash clear` |
| Delete specific stash | `git stash drop stash@{2}` |
