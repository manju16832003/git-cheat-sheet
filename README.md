# GIT cheat sheet

Git Cheat Sheet

#### Rename your local branch

`git branch -m new-name`

https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf

### Moving recent commits to a new branch
Assume that we accidently commited codes directly to master branch but later you would like to undo the commits and move out to a new branch

do the following
Note: Any changes not committed will be lost.
git branch newbranch      # Create a new branch, saving the desired commits
git reset --hard HEAD~3   # Move master back by 3 commits (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits

Reference: https://stackoverflow.com/questions/1628563/move-the-most-recent-commits-to-a-new-branch-with-git

## GIT

`git config user.name`
`git config --list`

#### Change your Git username
`git config --global user.name "Manjunath Reddy"` 

#### Change your Git email address
`git config user.email`
`git config --global user.email "manju16832003@gmail.com"`


### Git global setup

```git config --global user.name "Manjunath Reddy"
git config --global user.email "manju16832003@gmail.com"
```

#### Git Update Remote URL

`git remote set-url origin <url>`

#### Git Remove Romote

```
git remote -v
# View current remotes
origin  https://github.com/OWNER/REPOSITORY.git (fetch)
origin  https://github.com/OWNER/REPOSITORY.git (push)
destination  https://github.com/FORKER/REPOSITORY.git (fetch)
destination  https://github.com/FORKER/REPOSITORY.git (push)

git remote rm destination
# Remove remote
git remote -v
# Verify it's gone
origin  https://github.com/OWNER/REPOSITORY.git (fetch)
origin  https://github.com/OWNER/REPOSITORY.git (push)
```

### Git Push

`git push -u` -> The key is "argument-less git-pull". When you do a git pull from a branch, without specifying a source remote or branch, git looks at the branch.<name>.merge setting to know where to pull from. git push -u sets this information for the branch you're pushing.

Lets test

$ git checkout -b test

First, we push without -u:

```
$ git push origin test
$ git pull
You asked me to pull without telling me which branch you
want to merge with, and 'branch.test.merge' in
your configuration file does not tell me, either. Please
specify which branch you want to use on the command line and
try again (e.g. 'git pull <repository> <refspec>').
See git-pull(1) for details.

If you often merge with the same branch, you may want to
use something like the following in your configuration file:

    [branch "test"]
    remote = <nickname>
    merge = <remote-ref>

    [remote "<nickname>"]
    url = <url>
    fetch = <refspec>

See git-config(1) for details.
```

Now if we add -u:

```
$ git push -u origin test
Branch test set up to track remote branch test from origin.
Everything up-to-date
$ git pull
Already up-to-date.
```
