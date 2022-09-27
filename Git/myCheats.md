git documentation
==================

https://git-scm.com/docs

# shows the list of commits in one line format.
git log --oneline 
# displays a list of commits that contain the keyword in the message.
git log -S "keyword" 
# Displays a visual representation of how the branches and commits were created
# --oneline shortens output 
git log --oneline --graph

# create branch
git branch <branch-name>
# switch to branch
git checkout <branch-name>
# create and switch to branch
git checkout -b <branch-name>


# rename branch
git branch -M main

# shows current branch
git branch

git remote add origin _url_  
eg:  
git remote add origin https://github.com/thepunkduck/excursion.git  
git branch -M main  
git push -u origin main  
git pull 


# Discards changes in the working directory.
# puts file back to prev commit
git checkout HEAD filename
## or
git checkout -- filename

# Unstages file changes in the staging area.
git reset HEAD filename

# Resets to a previous commit in your commit history.
git reset commit_SHA

# allows you to correct mistakes and edit commits easily instead of creating a completely new one.
# git add filename, then amend 
 git commit --amend
# without message
git commit --amend --no-edit


git add filename
git add .  // all files

"SHA" stands for Simple Hashing Algorithm
shown for each commit!

# HEAD reset to this commitn SHA
git reset SHA

# GIT ALIAS COMMANDS
# examples
* git config --global alias.co "checkout"
* git config --global alias.br "branch"
* git config --global alias.glop "log --pretty=format:"%h %s" --graph"
* git config --global alias.l "log"

LOCAl repository
REMOTE repository (GitHub)

# push all the conmmits
git push  
git pull

# switch to master branch
git checkout master

# switch to other branch
git checkout branch_name

#  merge branch to master/main
git checkout master
git checkout main 

# merge conflict I
can switch branches with "checkout"
make edits, add and commit to any branch independantly

# merge conflict II
git checkout master
git merge fencing
   *we will get a conflict!*
_use code editor (nano)
resolve conflict
add file(s)
commit again_

# delete branch (after merge)
git branch -d branch_name

# delete branch that was never merged
git branch -D branch_name

# clone repository
git clone <url>
git clone remote_location clone_name


# command returns a verbose list of remote repositories that the current project is tied to.
$ git remote -v
origin  /home/ccuser/workspace/curriculum/science-quizzes/ (fetch)
origin  /home/ccuser/workspace/curriculum/science-quizzes/ (push)


git push origin branch-name

# command downloads objects from the origin remote repository. 
# not merged into the current branch-name branch. Instead, they are stored in the origin/branch-name branch, waiting to be merged.
git fetch
_merge like this_
git merge origin/master

# markdown
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet


# rebase
# rewrites history, merge preserves it
cd ..

to see the  remote branches you can use
git branch -r

git checkout -b branchName

 git branch -a

 Observe the new state of the branches, visually:

> git log --graph --decorate --oneline --all


Creating a .gitignore File
.gitignore is usually placed in the root directory of the repository. The filenames inside a .gitignore file can be written relative to the location of the .gitignore file. For example, we could add the line

src/main.js

We can ignore an entire directory by simply adding its name to .gitignore:

node_modules/

https://github.com/thepunkduck/practice-rebase-off-platform-project.git



create pull request instructions are not great
dont understand this (used in video, but not instruction in rep)::
git remote add upstream https://github.com/thepunkduck/practice-rebase-off-platform-project.git

create ISSUES
good for proj managments etc


GitHub CLI in action
# log in 
gh auth login
# create issue in one line
 gh issue create --title "Fix magic8.py error" --body "The code for magic8.py uses the Python random library without importing it. This causes issues during runtime."
# with prompts:
gh issue create
# list all opened issues so far
gh issue status
# fix issue

git checkout -b "fix-magic8"

# commits -a ??
git commit -a -m "proper import of random lib"
# what does this do??
# pushes named branch to repo
git push --set-upstream origin fix-magic8
#create pull request (follow prompts)
gh pr creategh repo clone thepunkduck/add-automated-tests-off-platform-project
#show status
gh issue status


# actions
mkdir .github

Then create another directory inside the .github directory and name it workflows. GitHub looks for the definitions of GitHub Actions inside this directory.

Create a new .yaml file inside the directory. Let’s name it unittests.yaml and
< see > add-automated-tests-off-platform-project\.github\workflows\unittests.yaml


The file introduces a new GitHub Action named Continuous Integration that is triggered on push

The action then runs the following steps in the order of their definition on an ubuntu-latest container: