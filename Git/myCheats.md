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


# rename branch
git branch -M main

# shows current branch
git branch

git remote add origin [url]
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


git push 
git pull

