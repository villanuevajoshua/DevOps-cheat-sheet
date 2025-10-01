# Git commands for merging a branch
Here is the sequence of Git commands for merging a branch from the source branch `development` to the target branch `staging`.

### Sequence of Git Command Line Interface (CLI) operations

| Step | Command | Description |
| - | - | - |
| 1. Switch to the target branch | `git checkout staging` | You must be on the branch you want to merge into. |
| 2. Pull the latest changes | `git pull origin staging` | Ensure your local staging is up-to-date with the remote before merging. |
| 3. Perform the squash merge | `git merge --squash development` | Merges all commits from development into your current branch (staging) as a single change in the staging area (index), but does not create a commit. |
| 4. Commit the squashed changes | `git commit -m "Squashed merge of feature from development"` | Creates the single commit on the staging branch. You can use a more descriptive message. |
| 5. Push the new commit | `git push origin staging` | Pushes the squashed commit to the remote staging branch. |
| 6. Delete the local source branch | `git branch -D development` | Deletes the local development branch. The uppercase -D is used to force deletion, as Git may not recognize a --squash merge as a "fully merged" branch (since there is no merge commit). |
| 7. Delete the remote source branch | `git push origin --delete development` | Deletes the development branch from the remote repository (e.g., origin). |
