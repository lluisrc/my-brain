### Setup
Set a name that is identifiable for credit when review version history
```terminal
git config --global user.name “[firstname lastname]”
```
Set an email address that will be associated with each history marker
```
git config --global user.email “[valid-email]”
```
Set automatic command line coloring for Git for easy reviewing
```
git config --global color.ui auto
```
---
### Setup and init
Initialize an existing directory as a Git repository
```
git init
```
Retrieve an entire repository from a hosted location via URL
```
git clone [url]
```
---
### Stage and spanshot
Show modified files in working directory, staged for your next commit
```
git status
```
Show modified files in working directory, staged for your next commit
```
add a file as it looks now to your next commit (stage)
```
Unstage a file while retaining the changes in working directory
```
git reset [file]
```
Diff of what is changed but not staged
```
git diff
```
Diff of what is staged but not yet commited
```
git diff --staged
```
Commit your staged content as a new commit snapshot
```
git commit -m “[descriptive message]”
```
---
### Brunch and merge
List your branches. a * will appear next to the currently active branch
```
git branch
```
Create a new branch at the current commit
```
git branch [branch-name]
```
Switch to another branch and check it out into your working directory
```
git checkout
```
Merge the specified branch’s history into the current one
```
git merge [branch]
```
Show all commits in the current branch’s history
```
git log
```
---
### Inspect and compare
Show the commit history for the currently active branch
```
git log
```
Show the commits on branchA that are not on branchB
```
git log branchB..branchA
```
show the commits that changed file, even across renames
```
git log --follow [file]
```
show the diff of what is in branchA that is not in branchB
```
git diff branchB...branchA
```
show any object in Git in human-readable format
```
git show [SHA]
```
---
### Tracking path changes
Delete the file from project and stage the removal for commit
```
git rm [file]
```
Change an existing file path and stage the move
```
git mv [existing-path] [new-path]
```
Show all commit logs with indication of any paths that moved
```
git log --stat -M
```
---
### Ignoring patterns
Save a file with desired paterns as .gitignore with either direct string matches or wildcard globs.
```
logs/ *.notes pattern*/
```
System wide ignore patern for all local repositories
```
git config --global core.excludesfile [file]
```
---
### Share and update
Add a git URL as an alias
```
git remote add [alias] [url]
```
Fetch down all the branches from that Git remote
```
git fetch [alias]
```
Merge a remote branch into your current branch to bring it up to date
```
git merge [alias]/[branch]
```
Transmit local branch commits to the remote repository branch
```
git push [alias] [branch]
```
Fetch and merge any commits from the tracking remote branch
```
git pull
```
---
### Rewrite history
Apply any commits of current branch ahead of specified one
```
git rebase [branch]
```
Clear staging area, rewrite working tree from specified commit
```
git reset --hard [commit]
```
---
### Temporaly commits
Save modified and staged changes
```
git stash
```
List stack-order of stashed file changes
```
git stash list
```
Write working from top of stash stack
```
git stash pop
```
Discard the changes from top of stash stack
```
git stash drop
```