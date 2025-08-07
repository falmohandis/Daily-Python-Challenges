
# GitHub Commands Cheat Sheet
# Make edits later


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