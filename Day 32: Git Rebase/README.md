The Nautilus application development team has been working on a project repository /opt/blog.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with DevOps team:


One of the developers is working on feature branch and their work is still in progress, however there are some changes which have been pushed into the master branch, the developer now wants to rebase the feature branch with the master branch without loosing any data from the feature branch, also they don't want to add any merge commit by simply merging the master branch into the feature branch. Accomplish this task as per requirements mentioned.

Also remember to push your changes once done.

---------------------------

git rebase is a powerful Git command used to integrate changes from one branch into another, creating a cleaner, linear project history than a typical merge. It essentially moves or combines a sequence of commits to a new base commit, rewriting the commit history in the process. 

Basic Usage

To rebase your current branch onto another branch (e.g., main): 

 1. Ensure you are on the branch you want to rebase (e.g., your feature branch).

    bash

    git switch feature-branch

2. Run the rebase command, specifying the target branch as the new base.

   bash

   git rebase main

Solution:

[root@ststor01 natasha]# cd /usr/src/kodekloudrepos/

[root@ststor01 kodekloudrepos]# ls -ltr

total 4

drwxr-xr-x 3 root root 4096 Feb  3 01:11 beta

[root@ststor01 kodekloudrepos]# cd beta/

[root@ststor01 beta]# ls -ltr

total 8

-rw-r--r-- 1 root root 34 Feb  3 01:11 info.txt

-rw-r--r-- 1 root root 22 Feb  3 01:11 feature.txt

[root@ststor01 beta]# git status

On branch feature

nothing to commit, working tree clean

[root@ststor01 beta]# git branch

* feature
  
  master
  
[root@ststor01 beta]# git log --oneline

3f22e4d (HEAD -> feature, origin/feature) Add new feature

f913a86 initial commit

[root@ststor01 beta]# git checkout master

Switched to branch 'master'

Your branch is up to date with 'origin/master'.

[root@ststor01 beta]# git log --oneline

a52f150 (HEAD -> master, origin/master) Update info.txt

f913a86 initial commit

[root@ststor01 beta]# git checkout feature

Switched to branch 'feature'

[root@ststor01 beta]# git rebase master

Successfully rebased and updated refs/heads/feature.

[root@ststor01 beta]# git log --oneline

406fdda (HEAD -> feature) Add new feature

a52f150 (origin/master, master) Update info.txt

f913a86 initial commit

[root@ststor01 beta]# git push origin feature

To /opt/beta.git

 ! [rejected]        feature -> feature (non-fast-forward)
 
error: failed to push some refs to '/opt/beta.git'

hint: Updates were rejected because the tip of your current branch is behind

hint: its remote counterpart. If you want to integrate the remote changes,

hint: use 'git pull' before pushing again.

hint: See the 'Note about fast-forwards' in 'git push --help' for details.

[root@ststor01 beta]# git push origin feature -f

Enumerating objects: 4, done.

Counting objects: 100% (4/4), done.

Delta compression using up to 16 threads

Compressing objects: 100% (2/2), done.

Writing objects: 100% (3/3), 296 bytes | 296.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To /opt/beta.git
 + 3f22e4d...406fdda feature -> feature (forced update)
