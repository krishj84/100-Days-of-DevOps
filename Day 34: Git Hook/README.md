The Nautilus application development team was working on a git repository /opt/demo.git which is cloned under /usr/src/kodekloudrepos directory present on Storage server in Stratos DC. The team want to setup a hook on this repository, please find below more details:

Merge the feature branch into the master branch, but before pushing your changes complete below point.

Create a post-update hook in this git repository so that whenever any changes are pushed to the master branch, it creates a release tag with name release-2023-06-15, where 2023-06-15 is supposed to be the current date. For example if today is 20th June, 2023 then the release tag must be release-2023-06-20. Make sure you test the hook at least once and create a release tag for today's release.

Finally remember to push your changes.
Note: Perform this task using the natasha user, and ensure the repository or existing directory permissions are not altered.

----------------------

Git hooks are scripts that run automatically when certain events occur in a Git repository, such as before or after a commit or push. They allow developers to automate tasks, enforce policies, and integrate with continuous integration/deployment (CI/CD) systems.

Solution:

[root@ststor01 demo.git]# pwd

/opt/demo.git

[root@ststor01 demo.git]# cd hooks/

[root@ststor01 hooks]# cat > post-update

#!/bin/bash

for refname in "$@"; do

  if [ "$refname" = "refs/heads/master" ]; then
  
    today=$(date +%F) 
    
    tag_name="release-${today}" # relase-2025-11-21

    newrev=$(git rev-parse "$refname")

    git tag -f "$tag_name" "$newrev"
    
  fi
  
done

[root@ststor01 hooks]# chmod 755 post-update

[root@ststor01 hooks]# cd /usr/src/kodekloudrepos/demo/

[root@ststor01 demo]# git branch

* feature
* 
  master
  
[root@ststor01 demo]# ls

feature.txt  info.txt

[root@ststor01 demo]# git log --oneline

fe9ff73 (HEAD -> feature, origin/feature) Add feature

df490d4 (origin/master, master) initial commit

[root@ststor01 demo]# git checkout master

Switched to branch 'master'

Your branch is up to date with 'origin/master'.

[root@ststor01 demo]# git log --oneline

df490d4 (HEAD -> master, origin/master) initial commit

[root@ststor01 demo]# git merge feature

Updating df490d4..fe9ff73

Fast-forward

 feature.txt | 1 +
 
 1 file changed, 1 insertion(+)
 
 create mode 100644 feature.txt
 
[root@ststor01 demo]# git log --oneline

fe9ff73 (HEAD -> master, origin/feature, feature) Add feature

df490d4 (origin/master) initial commit


[root@ststor01 demo]# cd /opt/demo.git/

[root@ststor01 demo.git]# git tag


Update info.txt

[root@ststor01 demo.git]# cd /usr/src/kodekloudrepos/demo/

[root@ststor01 demo]# vi info.txt 

[root@ststor01 demo]# cat info.txt 

Welcome to xFusionCorp Industries
Update

[root@ststor01 demo]# git status

On branch master

Your branch is ahead of 'origin/master' by 1 commit.

  (use "git push" to publish your local commits)

Changes not staged for commit:

  (use "git add <file>..." to update what will be committed)
  
  (use "git restore <file>..." to discard changes in working directory)
  
        modified:   info.txt

no changes added to commit (use "git add" and/or "git commit -a")

[root@ststor01 demo]# git add --all

[root@ststor01 demo]# git commit -m "Updated again"

[master 6410fc7] Updated again

 1 file changed, 1 insertion(+), 1 deletion(-)
 
[root@ststor01 demo]# git push origin master

Enumerating objects: 5, done.

Counting objects: 100% (5/5), done.

Delta compression using up to 16 threads

Compressing objects: 100% (2/2), done.

Writing objects: 100% (3/3), 320 bytes | 320.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)

To /opt/demo.git

   d825489..6410fc7  master -> master
   
[root@ststor01 demo]# cd /opt/demo.git/

[root@ststor01 demo.git]# git tag

release-2026-02-04

[root@ststor01 demo.git]# 

