# gittology
A test repository to learn GIT basics (commit/pull/push/branch/merge)

### Why

Out of sheer necessity we needed a way to let other team members, like designers, a way to test basic GIT actions (committing and pushing files, pulling from a repository). As always practice makes perfect, so I decided to create a GitHub repository for testing purposes.

### Structure

Ideally we have different meaningful branches that can be used to perform the basic GIT operations, plus it could be used to experience the most basic case of conflict, rebase and squashed merge.

### How

`$ git clone https://github.com/Objectway/gittology.git`

### Repository structure

The repository consists of 4 branches:
- master
- merge-conflict
- merge-master
- merge-standard

Any of them cover the most basic set of standard operations, starting from a simple merge to the most complex case of a conflict while merging.

### Preparation

Fire up your terminal and `$ cd` in your repository folder, **let's suppose that you've cloned it on your home directory**:

`$ cd ~/gittology`


## Standard operations
### CHECKING BRANCHES

You are now on the `master` branch, which is the name of the default branch created by Git, as per convention is the main branch.

`$ git branch -a` _show branches { local and remote }_

Should return something like that

```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
  remotes/origin/merge-conflict
  remotes/origin/merge-master
  remotes/origin/merge-standard
```

### COMMIT

A brief check of the files contained in the repository, you should see a list of files like this one:

`$ ls -l`

```
-rw-------  1 jenoma  staff  1077 Jul 28 15:48 LICENSE
-rw-r--r--  1 jenoma  staff   678 Jul 28 15:49 README.md
-rw-r--r--  1 jenoma  staff   493 Jul 28 15:48 file_1.md
-rw-r--r--  1 jenoma  staff   493 Jul 28 15:48 file_2.md
-rw-r--r--  1 jenoma  staff   345 Jul 28 15:49 file_3.md
```

Open `file_1.md`__*__ with your editor of choice and start adding a couple of random lines of written text.

_* .md is a markdown file, you can open it with a markdown capable editor or as a plain text file_

Now you should check the status of the repository with:

`$ git status`

```
[genoma:~/gittology-test]$ git status                                                                                                                                                                                                                                                                              (master✱)
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file_1.md

no changes added to commit (use "git add" and/or "git commit -a")
[genoma:~/gittology-test]$                                                                                                                                                                                                                                                                                         (master✱)
```

The changes, as your terminal is clearly telling you, are not __staged__ for commit: __this means that you have to add files into the stage area to commit them__.

And that brings us to the next step:

`$ git add -A` _add file/s to the stage area { add all files }_

Than you should do the actual commit:

`$ git commit -m 'added file'` _commit the staged file/s { with the commit message 'added files' }_

__IMPORTANT: the commit message is mandatory, if you don't provide the -m option it will be used Vi as the default editor to provide it.__


### PUSH and PULL

As you should know, your commits are local until they are pushed to the remote repository:

`$ git push origin master` _push to the remote origin, branch master_

Usually before pushing, if you are working in a team and on the same repo/branch you should do a pull before a push, because if something has changed on the remote repository while you were working Git will politely throws you an error asking to pull before push.

`$ git pull origin master` _pull from the remote origin, branch master_

`$ git push origin master` _push to the remote origin, branch master_

#### CAVEAT

`git branch --set-upstream origin master` allows to track the branch in which you are with the specified remote/branch: _<u>permits to omit the remote/branch declaration when pushing/pulling: `$ git pull` and `$ git push`</u>_


### MERGE

This repository has been developed with some basic merge cases between branches:

- merge-conflict
- merge-master
- merge-standard

Those three are the branches that we will use to test some merge testing.

> Incorporates changes from the named commits (since the time their histories diverged from the current branch) into the current branch. ([git-scm](http://git-scm.com/docs/git-merge))

In few words it git-merge merges the changes from a branch to another.

While on master branch:

`$ git fetch origin merge-standard:merge-standard` _get the remote branch merge-standard and put it as a local branch with the same name._

`$ git merge merge-standard` _merge merge-standard into the branch i'm on right now_

Merge standard is a simple merge without any sort of conflict, basically it should be painless and a straight forward process.

#### [more to come]
