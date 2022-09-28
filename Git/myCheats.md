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
# to repo
gh pr creategh repo clone thepunkduck/add-automated-tests-off-platform-project
# to wherever
gh pr create --fill
#show status
gh issue status



# actions
mkdir .github

Then create another directory inside the .github directory and name it workflows. GitHub looks for the definitions of GitHub Actions inside this directory.

Create a new .yaml file inside the directory. Let’s name it unittests.yaml and
< see > add-automated-tests-off-platform-project\.github\workflows\unittests.yaml


The file introduces a new GitHub Action named Continuous Integration that is triggered on push

The action then runs the following steps in the order of their definition on an ubuntu-latest container:

# to show difference in local branch and repo
 git diff origin/main rsvp-james


 gitignore::
 .gitignore
   eg: binaries, sensitive file etc


// stuff added
   git diff --cached

// all commited
   git commit -am message


   

git add * means add all files in the current directory, except for files whose name begin with a dot. This is your shell functionality and Git only ever receives a list of files.

git add . has no special meaning in your shell, and thus Git adds the entire directory recursively, which is almost the same, but including files whose names begin with a dot.


after clone,
then commit pull request


github insights - show work done

resolving conflicts on pull requests
merge

local : do git pull


git blame <file>







// so that git push knows where the upstream is coming from
 git config --global push.default current



The answer to the question you asked—which I'll rephrase a bit as "do I have to set an upstream"—is: no, you don't have to set an upstream at all.

If you do not have upstream for the current branch, however, Git changes its behavior on git push, and on other commands as well.

The complete push story here is long and boring and goes back in history to before Git version 1.5. To shorten it a whole lot, git push was implemented poorly.1 As of Git version 2.0, Git now has a configuration knob spelled push.default which now defaults to simple. For several versions of Git before and after 2.0, every time you ran git push, Git would spew lots of noise trying to convince you to set push.default just to get git push to shut up.

You do not mention which version of Git you are running, nor whether you have configured push.default, so we must guess. My guess is that you are using Git version 2-point-something, and that you have set push.default to simple to get it to shut up. Precisely which version of Git you have, and what if anything you have push.default set to, does matter, due to that long and boring history, but in the end, the fact that you're getting yet another complaint from Git indicates that your Git is configured to avoid one of the mistakes from the past.

What is an upstream?

An upstream is simply another branch name, usually a remote-tracking branch, associated with a (regular, local) branch.

Every branch has the option of having one (1) upstream set. That is, every branch either has an upstream, or does not have an upstream. No branch can have more than one upstream.

The upstream should, but does not have to be, a valid branch (whether remote-tracking like origin/B or local like master). That is, if the current branch B has upstream U, git rev-parse U should work. If it does not work—if it complains that U does not exist—then most of Git acts as though the upstream is not set at all. A few commands, like git branch -vv, will show the upstream setting but mark it as "gone".

What good is an upstream?

If your push.default is set to simple or upstream, the upstream setting will make git push, used with no additional arguments, just work.

That's it—that's all it does for git push. But that's fairly significant, since git push is one of the places where a simple typo causes major headaches.

If your push.default is set to nothing, matching, or current, setting an upstream does nothing at all for git push.

(All of this assumes your Git version is at least 2.0.)

The upstream affects git fetch

If you run git fetch with no additional arguments, Git figures out which remote to fetch from by consulting the current branch's upstream. If the upstream is a remote-tracking branch, Git fetches from that remote. (If the upstream is not set or is a local branch, Git tries fetching origin.)

The upstream affects git merge and git rebase too

If you run git merge or git rebase with no additional arguments, Git uses the current branch's upstream. So it shortens the use of these two commands.

The upstream affects git pull

You should never2 use git pull anyway, but if you do, git pull uses the upstream setting to figure out which remote to fetch from, and then which branch to merge or rebase with. That is, git pull does the same thing as git fetch—because it actually runs git fetch—and then does the same thing as git merge or git rebase, because it actually runs git merge or git rebase.

(You should usually just do these two steps manually, at least until you know Git well enough that when either step fails, which they will eventually, you recognize what went wrong and know what to do about it.)

The upstream affects git status

This may actually be the most important. Once you have an upstream set, git status can report the difference between your current branch and its upstream, in terms of commits.

If, as is the normal case, you are on branch B with its upstream set to origin/B, and you run git status, you will immediately see whether you have commits you can push, and/or commits you can merge or rebase onto.

This is because git status runs:

git rev-list --count @{u}..HEAD: how many commits do you have on B that are not on origin/B?
git rev-list --count HEAD..@{u}: how many commits do you have on origin/B that are not on B?
Setting an upstream gives you all of these things.

How come master already has an upstream set?

When you first clone from some remote, using:

$ git clone git://some.host/path/to/repo.git
or similar, the last step Git does is, essentially, git checkout master. This checks out your local branch master—only you don't have a local branch master.

On the other hand, you do have a remote-tracking branch named origin/master, because you just cloned it.

Git guesses that you must have meant: "make me a new local master that points to the same commit as remote-tracking origin/master, and, while you're at it, set the upstream for master to origin/master."

This happens for every branch you git checkout that you do not already have. Git creates the branch and makes it "track" (have as an upstream) the corresponding remote-tracking branch.

But this doesn't work for new branches, i.e., branches with no remote-tracking branch yet.

If you create a new branch:

$ git checkout -b solaris
there is, as yet, no origin/solaris. Your local solaris cannot track remote-tracking branch origin/solaris because it does not exist.

When you first push the new branch:

$ git push origin solaris
that creates solaris on origin, and hence also creates origin/solaris in your own Git repository. But it's too late: you already have a local solaris that has no upstream.3

Shouldn't Git just set that, now, as the upstream automatically?

Probably. See "implemented poorly" and footnote 1. It's hard to change now: There are millions4 of scripts that use Git and some may well depend on its current behavior. Changing the behavior requires a new major release, nag-ware to force you to set some configuration field, and so on. In short, Git is a victim of its own success: whatever mistakes it has in it, today, can only be fixed if the change is either mostly invisible, clearly-much-better, or done slowly over time.

The fact is, it doesn't today, unless you use --set-upstream or -u during the git push. That's what the message is telling you.

You don't have to do it like that. Well, as we noted above, you don't have to do it at all, but let's say you want an upstream. You have already created branch solaris on origin, through an earlier push, and as your git branch output shows, you already have origin/solaris in your local repository.

You just don't have it set as the upstream for solaris.

To set it now, rather than during the first push, use git branch --set-upstream-to. The --set-upstream-to sub-command takes the name of any existing branch, such as origin/solaris, and sets the current branch's upstream to that other branch.

That's it—that's all it does—but it has all those implications noted above. It means you can just run git fetch, then look around, then run git merge or git rebase as appropriate, then make new commits and run git push, without a bunch of additional fussing-around.

1To be fair, it was not clear back then that the initial implementation was error-prone. That only became clear when every new user made the same mistakes every time. It's now "less poor", which is not to say "great".

2"Never" is a bit strong, but I find that Git newbies understand things a lot better when I separate out the steps, especially when I can show them what git fetch actually did, and they can then see what git merge or git rebase will do next.

3If you run your first git push as git push -u origin solaris—i.e., if you add the -u flag—Git will set origin/solaris as the upstream for your current branch if (and only if) the push succeeds. So you should supply -u on the first push. In fact, you can supply it on any later push, and it will set or change the upstream at that point. But I think git branch --set-upstream-to is easier, if you forgot.

_There was a young lass of Aberdeen,
The changes from Git were her dream,
Scratched her head, wracked her brain,
Almost drove her insane,
She'd forgotten to set her upstream_
