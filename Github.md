Git is a distributed version control system (DVCS).
Let’s break that down:

Version control system (VCS) = a tool that tracks changes to files (usually code).
→ It lets you go back in time, compare versions, and collaborate safely.

Distributed = every developer has a full copy of the repository (not just a “client”).
→ You can work offline, commit locally, and sync later.

A repository is your project’s folder that Git tracks.
There are two kinds:

Local repository – on your computer (.git folder inside your project)

Remote repository – hosted on a server (e.g., GitHub, GitLab, Bitbucket)

🔁 Git Workflow Overview

Working Directory  →  Staging Area  →  Repository
     (edit)              (git add)        (git commit)
☁️ What Is GitHub?

GitHub is not Git itself — it’s a cloud hosting platform for Git repositories.
It adds features like:

Collaboration tools (Pull Requests, Issues)

Access control & team management

CI/CD workflows (GitHub Actions)

Project boards, discussions, etc.

You use Git locally, and GitHub remotely — they work together.
---------------------------------------------------------------------------------
GIT log:
     We can view all commits and commit history.
git log
git log -n 3
git log --oneline
---------------------------------------------------------------------------------
Git ignore:
       When you dont want to track any files 
->create a file names ".gitignore"(plane text file).
->add unnecessary files names in that file.
->now those files are not tracked by git.
---------------------------------------------------------------------------------
Git stash:
       Used to temporarily save our changes.
git stash--------->to save changes and stash them.
git stash list---->to list the stash's.
git stash apply--->Get back the changes.
---------------------------------------------------------------------------------
Git revert:
      The git revert command is used to undo a specific commit by creating a new commit that reverses the changes introduced by the old one — without deleting any history.
git revert <commit-id(get id from git log)>
Eg:git revert a1b2c3d
🪄 Revert the latest commit
git revert HEAD
---------------------------------------------------------------------------------
git reset:
      

🧠 Recap
Git Concept	You Use It For
git init	Create a new local repo
git clone	Copy a remote repo
git add	Stage changes
git commit	Save a snapshot
git push	Upload commits to GitHub
git pull	Fetch + merge remote changes
git branch	Manage versions of your work
git merge	Combine branches
---------------------------------------------------------------------------------
Branch:
create : git branch <name>
checkout : git checkout <name>
create and checkout : git checkout -b <name> (or) git switch -c <name>
know branch : git branch
Local Delete(safe delete) : git branch -d <branch-name>
            (Force delete): git branch -D <branch-name>
Delete branch remotely : git push origin --delete <branch-name>
---------------------------------------------------------------------------------
1. What is git merge?

Merging means combining the history of two branches.
For example, if you have:

main branch (stable code)

feature branch (new work)

and you want to bring changes from feature into main, you can do:
git checkout main
git merge feature

🔸 What happens:

Git takes the latest commits from both branches

Creates a new merge commit (if histories diverged)

Keeps both branches’ history intact

So the commit history looks like this:

A---B---C  (main)
     \
      D---E  (feature)


After merge:

A---B---C-------F  (main)
     \         /
      D-------E  (feature)


Here, F is the merge commit.

🔹 2. What is git rebase?

Rebasing means moving or reapplying commits from one branch onto another base commit.

Example:
You have:

A---B---C  (main)
     \
      D---E  (feature)


You can rebase feature onto main:

git checkout feature
git rebase main


Git takes commits D and E, and replays them on top of main:

A---B---C---D'---E'  (feature)


The commits D' and E' are new commits — same changes, different commit IDs.
