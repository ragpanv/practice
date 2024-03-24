# readme

git clone <link>
git status -- status of the branch
            -- shows in red i.e. file is not staged
            -- shows in green i.e. file is staging area

git add first.py -- this file is added to staging area. Later on staging area is used to commit files when we run git commit cmd

git commit -m "message" --changes are commited to your local version control
i.e. git commit adds the changes to local version control database.
we haven't pushed these changes to remote server (i.e. github here) 

git push -- to push changes in remote server

git difftool README.md -- to see changes done in file
-- it asks to launching for 'vimdiff' if difftool is not configured
-- to come out of vimdiff changes, type :qa (come out without saving)

### undoing the changes
#### undoing uncommited changes

- In first.py add println(1) and undo it.
