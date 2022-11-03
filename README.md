# git-lessons
## Command Line Basics
**Navigating**
- `ls`, `pwd`, `cd`, `cd/` to root directory, `cd~` to home directory, `cd ..`
- if folder has space, use backslash `\` e.g. `cd zz\ some\ directory` goes to the `Users/name/zz some directory` folder 

**Creating Deleting**
- create folders `mkdir <folder name>`
- create files `touch <file name 1>.<file extension> <file name2>.<file extension>`
- delete folders `rmdir <folder name 1> <folder name 2>`
- delete files `rm <file name 1>.<file extension> <file name2>.<file extension>`

**Deleting Files with Flags**
- flags add additiona options to your command
- `ls -s` displays file size
- `ls -l` provides more details
- `ls -ls` provides more details and displays file size
- `man ls`, `man rm` will show all the ls flags option available and all the remove options available
- to remove a folder and everything inside `rm -r practice`

**Copying & Moving Files & Folder**
- copy a file from old folder to new folder `cp <old folder name>/<file name 1> <new folder name>/`. if `/` is ommited, we new file or folder will be created instead.
- copy multiple files from old folder to new folder `cp -r <old folder name>/ <new folder name>/`. `-r` stands for recursive. 
- moving a file from old folder to new folder `mv <old folder name>/<file name 1> <new folder name>/`
- moving multiple files from old folder to new folder `mv -r <old folder name>/ <new folder name>/`
- renaming files with `mv`. `mv <old file name> <new file name>`

## Version Management Git
There are generally three git stages. Unstaged, staged, committed. The entire command is to navigate them.

**Git Commands**
- `git init` to create git
- `git status` to check current git status
- `git add .` to add all changes to git staging
- `git add <filename>` to add a changed file to git staging
- `git commit -m "<your message here>"` to commit changes from staging
- `git push` to push the committed git changes to a remote git
- `git log` to read all historical logs
- `git checkout <git id from git logs>` to see the old changes, then checkout with `git checkout master`
- `git checkout <branch name>` to change branch
- `git merge <branch name>` to merge the named branch with the branch that you are currently on
- `git switch <exiting branch name>` this will change to an existing branch
- `git switch -c <new branch name>` this will create a new branch and switch to it
- `git ls-files` shows the files in staging through `add .`
- `git rm <files>` to remove the file from staging

**Remove or undo unstaged changes**
- `git checkout <text file name to undo>` undo unstaged changes in one file
- `git checkout .` undo unstaged changes in all files
- `git restore <text file name to undo>` undo unstaged changes in one file
- `git restore .` undo unstaged changes in all files

**Remove or undo staged changes**
- `git reset <text file>` copy latest committed change to the staging. So this effectively reverses stage changes. Then use `git checkout <text file>`
- `git restore --staged <text file>` then use `git checkout <text file>` to unstage the staged changes

**Remove or undo committed changes**
- `git reset --soft HEAD~1` this reverts the commit by one step. if it is `2` then reverts the commit by two step. but retain the changes in the working directory or staged changes.
- `git reset --hard HEAD~1` reverts the commit and also remove the staged changes

**Deleting branches**
- `git branch -D <branch name>`

**Committing detached head changes**
- From the master branch, after switching to a previous commit as a detached head, then you make changes to that commit, stage it then commit it, you will effectively create another branch just for that detached head. But requires you to explicit create a branch with `git branch <new-branch-name> <detached HEAD ID>`, then you can merge with master with `git merge <new-branch-name>`

**.gitignore**
- Add file path into `.gitignore` file to ignore a certain file
- use `*.<file-format>` to ignore all files of that format
- user `!<file-name>` to say that this file shouldn't be ignored

## Advance Git
**Saving progress without staging and committing**
- `git stash` to save unstaged and uncommited files
- `git stash push -m "<stash message>"` to save a stash with message
- `git stash list` to list all the stashed files
- `git stash apply <number in the stash list>` to apply the saved stash. numbers are either `1`, `2` etc
- `git stash drop <number>` to delete selected stash
- `git stash clear` to delete all stash.
- `git reflog` to see an overview of all the changes applied to a branch, rolling back 30 days. Can then use detached head instructions above to renable lost branches

**Fast Forward Type Merge**
No additional commit in master branch. The non-master branch can then merge with the master branch

**Recursive Type Merge**
There are additional commits in both the master and the non-master branch.

**Rebase**
current branch is updated with the rebased branch. All commits and staging will be moved forward.
- `git rebase master` current branch rebase with master branch. If master branch is ahead of current branch, current branch will pull the commits that are ahead and put it before the current branch's commits and staging.
