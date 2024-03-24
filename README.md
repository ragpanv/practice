# readme

git clone <link>
git status -- status of the branch
            -- shows in red i.e. file is not staged
            -- shows in green i.e. file is in staging area

git add first.py -- this file is added to staging area. Later on staging area is used to commit files when we run git commit cmd

git commit -m "message" --changes are commited to your local version control
i.e. git commit adds the changes to local version control database.
we haven't pushed these changes to remote server (i.e. github here) 

git push -- to push changes in remote server

git difftool README.md -- to see changes done in file
-- it asks to launching for 'vimdiff' if difftool is not configured
-- to come out of vimdiff changes, type :qa (come out without saving)

### undoing the changes
#### undoing uncommited changes (file which are not staged, files are shown in red) i.e. before git add

- In first.py add println(1) and undo it.
on git status ->  (use "git add <file>..." to update what will be committed)
                  (use "git restore <file>..." to discard changes in working directory)
                   modified:   first.py
    so to undo it
    git restore first.py (restores it to previous version)
    [  git checkout -- first.py ]works same

    git status - show no changes as it is undone

- if multiple files are changed, to undo it use . as 
    git restore .
    git restore first.py README.md
    git checkout -- first.py README.md


#### undoing uncommited changes (file which are staged, file that are shown in green) i.e. after git add

git add first.py

 $ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   first.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md


git restore --staged first.py  --> first.py will be moved to unstaged area as below


On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   first.py

no changes added to commit (use "git add" and/or "git commit -a")


again user add cmd to add the required files to stagin area
$ git add README.md

#### undoing uncommited changes  (after git commit)

$ git add first.py
$ git commit -m 'added number line in py'
$ git log   -- to check commited details
commit commit id (HEAD -> main)  --> in local system
Author: abc
Date:   Sun Mar 24 21:28:26 2024 +0530

    added number 45

commit commit id (origin/main, origin/HEAD)  --> in remote
Author: abc
Date:   Sun Mar 24 21:27:22 2024 +0530

    added println(numbers)



-- git checkout or restore won't work as it is already commited
so revert cmd, it needs the commit id
git revert <commit id>   -- revert the change and commit it implicitly
it shows the reverting things, type :q

$ git log
commit commit id (HEAD -> main)
Author: abc
Date:   Sun Mar 24 21:29:14 2024 +0530

    #### Revert "added number 45"

    This reverts commit commit id.

commit commit id
Author: abc
Date:   Sun Mar 24 21:28:26 2024 +0530

    added number 45



if you want to just rever it ( commit when ever you want explicitly)
git revert -n commit_id ---> this reverts it and keep the previous latest in stagin area as below
git reset --hard commit id
HEAD is now at xxxxxxx asking age

$ git log (now the latest commit is asking age, commits done after this are gone now)