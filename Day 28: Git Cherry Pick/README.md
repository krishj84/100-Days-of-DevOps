The Nautilus application development team has been working on a project repository /opt/official.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with the DevOps team:

There are two branches in this repository, master and feature. One of the developers is working on the feature branch and their work is still in progress, however they want to merge one of the commits from the feature branch to the master branch, the message for the commit that needs to be merged into master is Update info.txt. Accomplish this task for them, also remember to push your changes eventually.

Solution:

The Git cherry-pick command is a powerful tool used to apply the changes from specific, individual commits on one branch to your currently active branch. This operation creates a new commit on the target branch with the same changes, rather than moving the original commit itself. 

How to Use git cherry-pick

The basic usage of the command line interface is straightforward. 

 1. Identify the commit hash: Use git log on the source branch to find the SHA-1 hash of the commit you want to apply. You can use git log  --oneline for a concise view.
 
 2. Switch to the target branch: Use git checkout <target-branch-name> to switch to the branch where you want the changes to be applied.
 
 3. Run the command: Execute git cherry-pick <commit-hash>. 
 
The changes will be applied as a new commit on your current branch. If conflicts arise, you must resolve them manually, stage the changes with git add ., and then run git cherry-pick --continue. To stop the operation entirely, use git cherry-pick --abort. 

[root@ststor01 natasha]# cd /usr/src/kodekloudrepos/news/

[root@ststor01 news]# git status
On branch feature

nothing to commit, working tree clean

[root@ststor01 news]# ls

info.txt  welcome.txt

[root@ststor01 news]# cat info.txt 

Welcome to xFusionCorp Industries!

[root@ststor01 news]# git log --oneline

a697137 (HEAD -> feature, origin/feature) Update welcome.txt

521de5b Update info.txt

37fa0d5 (origin/master, master) Add welcome.txt

ca068c9 initial commit

[root@ststor01 news]# git checkout master

Switched to branch 'master'

Your branch is up to date with 'origin/master'.

[root@ststor01 news]# git log --oneline

37fa0d5 (HEAD -> master, origin/master) Add welcome.txt

ca068c9 initial commit

[root@ststor01 news]# ls

info.txt  welcome.txt

[root@ststor01 news]# cat info.txt 

Welcome to xFusionCorp Industries

[root@ststor01 news]# git cherry-pick 521de5b

[master 26dda6b] Update info.txt

 Date: Fri Jan 30 19:07:45 2026 +0000
 
 1 file changed, 1 insertion(+), 1 deletion(-)
 
[root@ststor01 news]# git status

On branch master

Your branch is ahead of 'origin/master' by 1 commit.

  (use "git push" to publish your local commits)

nothing to commit, working tree clean

[root@ststor01 news]# git push origin master

Enumerating objects: 5, done.

Counting objects: 100% (5/5), done.

Delta compression using up to 16 threads

Compressing objects: 100% (2/2), done.

Writing objects: 100% (3/3), 314 bytes | 314.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)

To /opt/news.git

   37fa0d5..26dda6b  master -> master
   
[root@ststor01 news]# cat info.txt 

Welcome to xFusionCorp Industries!
