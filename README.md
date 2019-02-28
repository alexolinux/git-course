**GIT/GITHUB FOR BEGINNERS (ENVIRONMENT)**

    git config --global user.name "Alex"
    git config --global user.email "alexmendes@mymail.com"
    git config --global core.editor vim

**GETTING INFORMATION**

    git config --list --> Get information of all variables.
    git config user.name Alex
    git config user.email alexmendes@mymail.com

**STARTING A REPOSITORY**

Creating source folder in Server and enter it;
    "git init" to start the repo.
    
    EX.: 
    git init 
    Initialized empty Git repository in /git/git-course/.git/

NOTE:

    - hooks     --> Triggers to do certain actions during the project.
    - branch  	--> A branch in Git is simply a lightweight mobile example for one of these commits.
    - tag	    --> The tag is just a tag, in general, on a specific branch that marks a situation at a given time.

**LIFE CYCLE OF FILES:**

<< UNTRACKED > UNMODIFIED > MODIFIED > STAGED >>

**GIT REPOSITORY STATUS**

    git status

Nothing added to commit but untracked files present (use "git add" to track)

**ADD FILE TO GIT:**

    git add Readme.md
    new file:   Readme.md
	
NOTE: 
> WHENEVER THERE ARE FILE CHANGES, WE MUST USE "GIT ADD" AGAIN (BEFORE COMMIT --> TO STAGED). 

**GIT COMMIT**

git commit - Record changes to the repository

    git commit -m "Add Readme.md"

    [master (root-commit) 661c72d] Add Readme.md
    1 files changed, 2 insertions(+), 0 deletions(-)
    create mode 100644 Readme.md

**REVERTING CODE TO PREVIOUS STEP WITH git checkout AND git RESET**


* **git checkout**        - It's used to steps before commit actions.
* **git reset** <--level> - It's used to steps after commit actions.

**HOW TO**

01 - BEFORE EXECUTING 'git add' (staged phase):

(use "git checkout -- ..." to discard changes in working directory)

    git checkout <FILE>

02 - AFTER 'git add' (staged phase (ready to commit))

(use "git reset HEAD ..." to unstage)

    git reset HEAD <FILE>

**A LITTLE MORE ABOUT GIT "git reset"**

* **git reset** levels:
 
    git reset [--mixed | --soft | --hard | --merge | --keep] [-q] []

NOTE: 
> git reset always calls the previous HASH Commit. 

**OPTIONS:**

--soft	(CANCELS COMMIT, TAKE AWAY STAGE) Does not touch the index file nor the working tree at all, but requires them to be in a good order. This leaves all your changed files "Changes to be committed", as git status would put it.
    EX.: git reset --soft e3131b3f718e17c2014c528ba81e67dd16e232e4

--mixed	(CANCELS COMMIT, KEEP OUT STAGE(KEEP UNSTAGED))
       Resets the index but not the working tree (i.e.,
	   the changed files are preserved but not marked for commit) and reports
       what has not been updated. This is the default action.
	EX.:
	    git reset --mixed e3131b3f718e17c2014c528ba81e67dd16e232e4

--hard	(CANCELS COMMIT, UNDO ALL COMMIT CHANGES *)
     Matches the working tree and index to that of the tree being switched to.
	   "Any changes to tracked files in the working tree since <commit> are lost."

**GIT LOGS - OPTIONS**
***RUNNING COMMAND ON PROJECT DIRECTORY/REPOSITORY THAT YOU WANT TO CHECK OUT.**

    git log
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200

**LOG DETAILS**

    git log --decorate
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX (HEAD, master)
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200
    
    Add Readme.md

**LOG - FILTER BY AUTHOR**

    git log --author="Alex"

**LOG WITH COLABORATORS**

    git shortlog
    Alex (2):
    
    Add Readme.md
    Updating Readme.md

    git shortlog -sn
	2  Alex

**GRAPH LOG**

    git log --graph
        * commit ec98347a9312a0ec51c2967546ca48ba42c5a65cxX
        | Author: Alex <alexmendes@mymail.com>
        | Date:   Tue Nov 6 20:39:19 2018 -0200
        |
        |     Updating Readme.md
        |
        * commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
        Author: Alex <alexmendes@mymail.com>
        Date:   Mon Nov 5 23:36:04 2018 -0200

	Add Readme.md

**CHANGING DETAILS**

    git show <HASH_COMMIT>

    git show 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200

	Add Readme.md

**GETTING DIFFERENCES AND CHANGES**

    git diff

    diff --git a/Readme.md b/Readme.md

    new file mode 100644
    index 0000000..55e9705
    --- /dev/null
    +++ b/Readme.md
    @@ -0,0 +1,2 @@
    +# Github
    +Basic Study Repo GIT/GITHUB.
        git CHANGES
        git diff
        diff --git a/Readme.md b/Readme.md
    index fe17549..f401c3e 100644
    --- a/Readme.md
    +++ b/Readme.md
    @@ -1,4 +1,8 @@
    -###########
    -# Github ##
    -#06-11-2018
    +#########################
    +# Github                #
    +# https://git-scm.com/  #
    +# 06-11-2018            #
    +#_______________________#
    +#########################
    +
    Basic Study Repo GIT/GITHUB.

**GIT NAME ONLY**

    git diff --name-only
    	Readme.md

**WORKING WITH REMOTE REPOS.**

Create a new repository on the command line

    echo "# git-course" >> README.md
    git init git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:alexmbarbosa/git-course.git git push -u origin master

Push an existing repository from the command line

    git remote add origin git@github.com:alexmbarbosa/git-course.git
    git push -u origin master

**CHECKING FOR REPOSITORY EXISTENCE**

    git remote show origin <- Output Command.

**VERBOSE MODE**

    git remote -v

    origin git@github.com:alexmbarbosa/git-course.git (fetch)
    origin git@github.com:alexmbarbosa/git-course.git (push)

**RECEIVING CODE FROM REMOTE REPO TO LOCAL REPO**

    git pull [<options>] [<repository> [<refspec>…]]

git pull incorporates changes from a remote repository into the current branch.
In its default mode, git pull is shorthand for git fetch followed by git merge FETCH_HEAD.

    git pull
    remote: Enumerating objects: 17, done.
    remote: Counting objects: 100% (17/17), done.
    remote: Compressing objects: 100% (10/10), done.
    remote: Total 15 (delta 5), reused 0 (delta 0)
    Unpacking objects: 100% (15/15), done.
    From http://zabhx02b/ga/git-course
       ca066cb..c3de5a7  master     -> origin/master
    Updating ca066cb..c3de5a7
    Fast-forward
     README.md | 13 +++++++++++--
     1 file changed, 11 insertions(+), 2 deletions(-)

**CLONING git PROJECTS**

git clone - Clone a repository into a new diretory.

**git clone PROTOCOLS**

    * ssh://[user@]host.xz[:port]/path/to/repo.git
    * git://host.xz[:port]/path/to/repo.git
    * http[s]://host.xz[:port]/path/to/repo.git
    * ftp[s]://host.xz[:port]/path/to/repo.git

Example:

    git clone user@host.xz:path/to/repo.git/

**UNDERSTANDING FORK CONCEPTS**

A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project.
Most commonly, forks are used to either propose changes to someone else's project or to use someone else's project as a starting point for your own idea.

![alt text](https://help.github.com/assets/images/help/repository/fork_button.jpg)

**WHAT IS A BRANCH?**

Git branches are effectively a pointer to a snapshot of your changes. When you want to add a new feature or fix a bug—no matter how big or how small—you spawn a new branch to encapsulate your changes. 
This makes it harder for unstable code to get merged into the main code base, and it gives you the chance to clean up your future's history before merging it into the main branch.

git-branch - List, create, or delete branches.
The git branch command lets you create, list, rename, and delete branches.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:746be214-eb99-462c-9319-04a4d2eeebfa/01.svg)

It doesn’t let you switch between branches or put a forked history back together again. 
For this reason, git branch is tightly integrated with the git checkout and git merge commands.

**git branch COMMON OPTIONS**

List all of the branches in your repository. This is synonymous with git branch --list.

    git branch

Create a new branch called <branch>. This does not check out the new branch.

    git branch <branch>

Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

    git branch -d <branch>

Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

    git branch -D <branch>

Deleting remote branches in git. To delete a remote branch, we do not use the "git branch" command - but instead "git push" with the "--delete" flag:

    git push <remote_name> :<branch_name>
    git push origin --delete feature/login
    
Rename the current branch to <branch>.

    git branch -m <branch>

List all remote branches.

    git branch -a
    
Create a new branch <new> referencing <start-point>, and check it out.

    git checkout -b <new> <start-point>
    
**NOTES ABOUT BRANCHES**

If you are creating a branch that you want to checkout immediately, it is easier to use the git checkout command with its -b option to create a branch and check it out with a single command.

The options --contains, --no-contains, --merged and --no-merged serve four related but different purposes:

    --contains <commit> is used to find all branches which will need special attention if <commit> were to be rebased or amended, since those branches contain the specified <commit>.
    --no-contains <commit> is the inverse of that, i.e. branches that don’t contain the specified <commit>.
    --merged is used to find all branches which can be safely deleted, since those branches are fully contained by HEAD.
    --no-merged is used to find branches which are candidates for merging into HEAD, since those branches are not fully contained by HEAD.
    
**HANDLING BRANCHES**

git checkout - Switch branches or restore working tree files.

Updates files in the working tree to match the version in the index or the specified tree. If no paths are given, git checkout will also update HEAD to set the specified branch as the current branch.

    git checkout <branch>

To prepare for working on <branch>, switch to it by updating the index and the files in the working tree, and by pointing HEAD at the branch. 
Local modifications to the files in the working tree are kept, so that they can be committed to the <branch>.

If <branch> is not found but there does exist a tracking branch in exactly one remote (call it <remote>) with a matching name, treat as equivalent to:

    git checkout -b <branch> --track <remote>/<branch>
	
Specifying -b causes a new branch to be created as if git branch were called and then checked out.

    git checkout -b|-B <new_branch> [<start point>]

If -B is given, <new_branch> is created if it doesn’t exist; otherwise, it is reset.

**JOIN BRANCHES**

There are two different ways for joining branches:
- git merge
- git rebase

**git merge**

git merge will combine multiple sequences of commits into one unified history. In the most frequent use cases, git merge is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, git merge takes two commit pointers, usually the branch tips, and will find a common base commit between them.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:86eba9ec-9391-45ea-800a-948cec1f2ed7/Branch-2.png)

Invoking this command will merge the specified branch feature into the current branch, we'll assume master. Git will determine the merge algorithm automatically (discussed below).

![alt text](https://wac-cdn.atlassian.com/dam/jcr:83323200-3c57-4c29-9b7e-e67e98745427/Branch-1.png)

Merge commits are unique against other commits in the fact that they have two parent commits. When creating a merge commit Git will attempt to auto magically merge the separate histories for you.

**git merge - BEFORE AND AFTER**

![alt text](https://wac-cdn.atlassian.com/dam/jcr:91b1bdf5-fda3-4d20-b108-0bb9eea402b2/08.svg)

In example above it demonstrates a fast-forward merge. The code below creates a new branch, adds two commits to it, then integrates it into the main line with a fast-forward merge.

    # Start a new feature
    git checkout -b new-feature master
    # Edit some files
    git add <file>
    git commit -m "Start a feature"
    # Edit some files
    git add <file>
    git commit -m "Finish a feature"
    # Merge in the new-feature branch
    git checkout master
    git merge new-feature
    git branch -d new-feature

**MERGING WITH git merge**

A merge happens when combining two branches. Git will take two (or more) commit pointers and attempt to find a common base commit between them.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg)

![alt text](https://wac-cdn.atlassian.com/dam/jcr:2d3aef7f-6e1d-4e39-a5a5-97dd7714fdd2/what-is-a-merge.gif)

**git rebase**

Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow. The general process can be visualized as the following:

![alt text](https://wac-cdn.atlassian.com/dam/jcr:e4a40899-636b-4988-9774-eaa8a440575b/02.svg)

From a content perspective, rebasing is changing the base of your branch from one commit to another making it appear as if you'd created your branch from a different commit. Internally, Git accomplishes this by creating new commits and applying them to the specified base.
It's very important to understand that even though the branch looks the same, it's composed of entirely new commits.

**The Rules about git rebase**

Rebase has the advantage that there is no merge commit created. However, because HEAD is not a descendant of the pre-rebase HEAD commit, rebasing can be problematic.

- Rule One: Never Rebase Public Branches
- Rule Two: Committing When Branch Change on Remote

The example below combines git rebase with git merge to maintain a linear project history. This is a quick and easy way to ensure that your merges will be fast-forwarded.

    # Start a new feature
    git checkout -b new-feature master
    # Edit files
    git commit -a -m "Start developing a feature"

In the middle of our feature, we realize there’s a security hole in our project:

    # Create a hotfix branch based off of master
    git checkout -b hotfix master
    # Edit files
    git commit -a -m "Fix security hole"
    # Merge back into master
    git checkout master
    git merge hotfix
    git branch -d hotfix

After merging the hotfix into master, we have a forked project history. Instead of a plain git merge, we’ll integrate the feature branch with a rebase to maintain a linear history:

    git checkout new-feature
    git rebase master

This moves new-feature to the tip of master, which lets us do a standard fast-forward merge from master:

    git checkout master
    git merge new-feature

**GIT RECAPPING: MERGE vs REBASE**

**Merging**

When you run git merge, your HEAD branch will generate a new commit, preserving the ancestry of each commit history.

![alt text](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/673b91456bdc6fd454c5ad203f825568/git-merge-2.png)

Fast forward merge is a type of merge that doesn't create a commit, instead, it updates the branch pointer to the last commit.

Pros:

1- Simple to use and understand.
2- The commits on the source branch remain separate from other branch commits. This separation can be useful in the case of feature branches, where you might want to take a feature and merge it into another branch later.
3- Existing commits on the source branch are unchanged and remain valid. It doesn’t matter if they have been shared with others.

Cons:

1- History can become polluted by lots of merge commits.
2- Visual charts of your repository can have non-informative branch lines.

**Rebasing**

The rebase re-writes the changes of one branch onto another without creating a new commit.
For every commit that you have on the feature branch and not in the master, a new commit will be created on top of the master. It will appear as if those commits were written on top of master branch all along.

![alt text](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/5ade4f7276bc6ad18dad4b6078950ac9/git-rebase.png)

Pros:

1- Simplifies your history and visual charts.

Cons:

1- In Git, you may push commits you may want to rebase later (as a backup) but only if it’s to a remote branch that only you use. If anyone else checks out that branch and you later rebase it, it’s going to get very confusing.
2- Each commit is rebased in order, and a conflict will interrupt the process of rebasing multiple commits. With a conflict, you have to resolve the conflict in order to continue the rebase.

**git merge OR git rebase? Which one should I use?**

Following factors should be considered when choosing which operation to use:

1- If you are planning to re-integrate a completed feature branch, use merge.
2- If you have already pushed the branch you are working on, then you should not rebase but merge instead. For branches that have not been pushed, rebase, test and merge.
3- If you are working on a shared branch or an open source project along with many other developers outside of your team, don’t rebase. Since rebase destroys the branch and other developers will have inconsistent repositories.
4- If you think there is a chance you will want to revert some changes then use merge, since reverting a rebase is considerably difficult as compared to reverting a merge.

**.gitignore**

gitignore - Specifies intentionally untracked files to ignore.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:75f75cb6-a6ab-4f0b-ab29-e366914f513c/hero.svg)

A gitignore file specifies intentionally untracked files that Git should ignore. Files already tracked by Git are not affected; see the NOTES below for details.

git sees every file in your working copy as one of three things:

- tracked - a file which has been previously staged or committed;
- untracked - a file which has not been staged or committed;
- ignored - a file which Git has been explicitly told to ignore.

This Example below in order to exclude everything except a specific directory foo/bar (note the /* - without the slash, the wildcard would also exclude everything within foo/bar):

    $ cat .gitignore
    # exclude everything except directory foo/bar
    /*
    !/foo
    /foo/*
    !/foo/bar
    
**NOTES**

> The purpose of gitignore files is to ensure that certain files not tracked by Git remain untracked.
> To stop tracking a file that is currently tracked, use git rm --cached.


**git stash**

git stash - Stash the changes in a dirty working directory away.

Use git stash when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit.

    $ git status
    On branch master
    Changes to be committed:
    new file: style.css
    Changes not staged for commit:
    modified: index.html
    $ git stash
    Saved working directory and index state WIP on master: 5002d47 our new homepage
    HEAD is now at 5002d47 our new homepage
    $ git status
    On branch master
    nothing to commit, working tree clean

At this point you're free to make changes, create new commits, switch branches, and perform any other Git operations; then come back and re-apply your stash when you're ready.

**Tip Stash**
**Recovering stash entries that were cleared/dropped erroneously**

If you mistakenly drop or clear stash entries, they cannot be recovered through the normal safety mechanisms. However, you can try the following incantation to get a list of stash entries that are still in your repository, but not reachable any more:

    git fsck --unreachable |
    grep commit | cut -d\  -f3 |
    xargs git log --merges --no-walk --grep=WIP

**Git Aliases**

Alias provides easily set up an alias for each command using git config. Here are a couple of examples you may want to set up:

    $ git config --global alias.co checkout
    $ git config --global alias.br branch
    $ git config --global alias.ci commit
    $ git config --global alias.st status

**Git Tagging**

Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (v1.0, v2.0 and so on). In this section, you’ll learn how to list existing tags, how to create and delete tags, and what the different types of tags are.

**Listing Your Tags**

Listing the existing tags in Git is straightforward. Just type git tag (with optional -l or --list):

    $ git tag
    v1.0
    v2.0

This command lists the tags in alphabetical order; the order in which they are displayed has no real importance.

You can also search for tags that match a particular pattern. The Git source repo, for instance, contains more than 500 tags. If you’re interested only in looking at the 1.8.5 series, you can run this:

    $ git tag -l "v1.8.5*"
    v1.8.5
    v1.8.5-rc0
    v1.8.5-rc1
    v1.8.5.1
    v1.8.5.3

**Creating Tags**

Git supports two types of tags: lightweight and annotated.

A lightweight tag is very much like a branch that doesn’t change?—?it’s just a pointer to a specific commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

**Annotated Tags**
Creating an annotated tag in Git is simple. The easiest way is to specify -a when you run the tag command:

    $ git tag -a v1.4 -m "my version 1.4"
    $ git tag
    v0.1
    v1.3
    v1.4

The -m specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

**Deleting Tags**
To delete a tag on your local repository, you can use git tag -d <tagname>. For example, we could remove our lightweight tag above as follows:

    $ git tag -d v1.4-lw
    Deleted tag 'v1.4-lw' (was e7d5add)

Note that this does not remove the tag from any remote servers. There are two common variations for deleting a tag from a remote server.

The way to interpret the above is to read it as the null value before the colon is being pushed to the remote tag name, effectively deleting it.

The second (and more intuitive) way to delete a remote tag is with:

    $ git push origin --delete <tagname>

In order to delete remote tags, the first variation is: 

    git push <remote> :refs/tags/<tagname>:
    $ git push origin :refs/tags/v1.4-lw
    To /git@github.com:schacon/simplegit.git
        - [deleted]         v1.4-lw

Other alternative:

    git push --delete origin tagname
    git tag -d tagname

**git revert**

git revert - Revert some existing commits.

Given one or more existing commits, revert the changes that the related patches introduce, and record some new commits that record them. 
This requires your working tree to be clean (no modifications from the HEAD commit).

The git revert command can be considered an 'undo' type command, however, it is not a traditional undo operation. Instead of removing the commit from the project history, it figures out how to invert the changes introduced by the commit and appends a new commit with the resulting inverse content.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:b6fcf82b-5b15-4569-8f4f-a76454f9ca5b/03%20(7).svg)

**git revert examples:**

Revert the changes specified by the fourth last commit in HEAD and create a new commit with the reverted changes.

	git revert HEAD~3

Revert the changes done by commits from the fifth last commit in master (included) to the third last commit in master (included), but do not create any commit with the reverted changes. The revert only modifies the working tree and the index.

	git revert -n master~5..master~2
	
**Resetting vs Reverting**

It's important to understand that git revert undoes a single commit—it does not "revert" back to the previous state of a project by removing all subsequent commits. 
In Git, this is actually called a reset, not a revert.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:a6a50d78-48e3-4765-8492-9e48dec8fd2f/04%20(2).svg)


    
**REFERENCES:**

	- <https://pt.stackoverflow.com/questions/80583/qual-%C3%A9-a-diferen%C3%A7a-entre-um-branch-e-uma-tag>
	- <https://git-scm.com/book/pt-br/v1/Ramifica%C3%A7%C3%A3o-Branching-no-Git-O-que-%C3%A9-um-Branch>
	- <https://www.udemy.com/git-e-github-para-iniciantes>
	- <https://br.atlassian.com/git/tutorials/>
	- <https://git-scm.com/docs/user-manual.htmlh>
    - <http://ndpsoftware.com/git-cheatsheet.html>
    - <https://www.git-tower.com/learn/git/faq/delete-remote-branch>
