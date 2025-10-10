# Git commands

## Introduction
Git is a widely used, free, and open-source distributed version control system designed to efficiently track changes in files and coordinate work among multiple people on a software project.

---

### Git global auth/credentials
```bash
git config --global user.email <your_email>
git config --global user.name <your_name>
```

### Git remote auth/credentials
```bash
git config user.email <your_email>
git config user.name <your_name>
```

### Generate SSH
```
ssh-keygen -t rsa -b 4096 -C <your_optional_comment>
```

### Verify Authentication

To check the list of all configurations, including user-related configurations:
```bash
git config --global --list
```

## Useful commands

- **Fetch and Prune**: This is the most common method. It fetches all the latest changes from the remote and simultaneously prunes the deleted branches
```bash
git fetch --prune
```

- **Prune Only**: If you don't need to fetch new changes and want to clean up, you can use
```bash
git remote prune
```

### Update git

update default branch, from `master ` to `main`
```bash
git branch -m master main
git fetch origin
git branch -u main main
git remote set-head origin -a
```

If the remote URL or branch name is incorrect, update it using the following commands
```bash
git remote set-url origin <new_remote_url>
git branch --set-upstream-to=origin/<correct_branch_name> main
```

### How to ignore all files and folders
```bash
*
!*gitignore
```

### How to revert a commit with SHA
```bash
git revert -m 1 <SHA>
```

