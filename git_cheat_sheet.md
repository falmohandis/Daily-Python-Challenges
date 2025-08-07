
# GitHub Commands Cheat Sheet

# 🌐 Git + GitHub Cheat Sheet (Visual Studio Focused)

---

## 🔰 Initial Setup (First Time Using GitHub Repo)

```sh
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

If starting a new repo from scratch:

```sh
git init
git remote add origin https://github.com/<your-username>/<repo-name>.git
```

---

## 🧱 First Commit (Initial Commit)

```sh
git add --all
git commit -m "Initial commit"
git push -u origin main
```

> `-u` sets the upstream so future pushes can just be `git push`.

---

## 🔁 Regular Commit Workflow

```sh
git status              # Check what’s changed
git add .               # Stage all changes
git commit -m "Your message here"
git push                # Push to the current tracked branch
```

---

## ⚠️ Handling Merge Conflicts (Rebase Workflow Recommended)

```sh
git pull origin main --rebase
```

> Keeps your history clean by replaying your commits on top of the latest `main`.

### If Rebase Fails:

```sh
git rebase --abort                # Cancel rebase and return to previous state
rm -rf ".git/rebase-merge"        # Remove leftover rebase state if still stuck
```

### Force Push After Rebase:

```sh
git push --force-with-lease
```

> ✅ Safer than `--force`, as it only pushes if remote hasn’t changed unexpectedly.

---

## 🗑️ Cleaning Up Untracked Files

```sh
git clean -fd
```

- `-f`: force (required for destructive actions)
- `-d`: include untracked directories

> Useful for removing temp files, build artifacts, etc.

---

## 🔄 Syncing Your Fork (If Using a Forked Repo)

```sh
git remote add upstream https://github.com/original-owner/repo.git
git fetch upstream
git checkout main
git rebase upstream/main
git push --force-with-lease
```

> Keeps your fork up to date with the original repo.

---

## 🧪 Checking Log & History

```sh
git log --oneline --graph --all
```

> Visual Studio also shows this in the **Git History** window for graphical view.

---

## 🔄 Switching Branches

```sh
git checkout -b new-feature          # Create and switch to new branch
git switch new-feature               # Switch (modern alternative)
git switch -c new-feature            # Create and switch in one go
```

To return to `main`:

```sh
git checkout main
```

---

## 📂 Stashing Changes (Temporary Work)

```sh
git stash                           # Save changes temporarily
git stash pop                       # Reapply latest stash
git stash list                      # View all stashes
git stash drop                      # Delete latest stash
```

> Great for quickly switching tasks without committing unfinished work.

---

## 🧼 Undoing Mistakes

### Undo last commit (but keep changes staged):

```sh
git reset --soft HEAD~1
```

### Undo last commit and unstage files:

```sh
git reset --mixed HEAD~1
```

### Discard changes in a file:

```sh
git checkout -- <file>
```

### Unstage a file:

```sh
git reset <file>
```

> Be cautious — some of these actions are **destructive** and cannot be undone.

---

## 🔍 See What’s Going On

```sh
git status              # Show staged and unstaged changes
git diff                # Show unstaged diffs
git diff --staged       # Show what's about to be committed
```

---

## 🧑‍💻 Git + Visual Studio Integration Tips

- Use the **Changes** tab to stage/commit files.
- Use the **Git menu** to Pull, Push, or Sync.
- **Merge conflicts** are shown with a 3-way merge editor.
- View history using the **Git Repository** window or right-click a file.

---

## 🛠 Configuring Git (Once per machine or repo)

```sh
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global pull.rebase true
git config --global core.autocrlf true   # Windows line endings
```

> These settings help Git behave consistently across machines and editors.

---

## ✅ Helpful Aliases (Optional Time Savers)

```sh
git config --global alias.s "status"
git config --global alias.c "commit -m"
git config --global alias.p "!git add . && git commit -m"
git config --global alias.l "log --oneline --graph --decorate --all"
```

> Aliases make frequently used commands shorter and faster.

---

## 💣 Emergency Commands (Use with Caution)

```sh
git reset --hard           # Discard ALL changes and commits since last commit
git clean -fd              # Remove all untracked files and directories
```

> ⚠️ These commands are **destructive** and will **permanently delete** changes.













# older version


# Delete all untracked files

## Initial Commit (First Time Setup)

```sh
git add --all
git commit -m "<your commit message>"
git push --force origin main
```

## Subsequent Commits

```sh
git add --all
git commit -m "<your commit message>"
git push --force origin main
```

## Resolving Push Conflicts (Rebase Workflow) 

```sh
git pull origin main --rebase
# If you encounter rebase errors and need to abort:
git rebase --abort
# If necessary, you can remove the rebase merge state:
rm -rf ".git/rebase-merge"
# To force push your changes (use with caution):
git push --force origin main
```

**Note:**  
- Use `git push --force` only if you are sure you want to overwrite the remote branch.
- Always resolve conflicts carefully to avoid data








# Github commands for managing a repository
#first time doing it

git add --all
git commit -m "<your_message_here>"
git push origin main


#after doing a first commit in your repo

git add --all
git commit -m "<your_message_here>"
git push 


#if shit fucks up, you gotta rebase that hoe
git pull origin main --rebase
    #if its rebased already and gives an error, remove the rebase file
    rm -fr ".git/rebase-merge"
git push --force origin main