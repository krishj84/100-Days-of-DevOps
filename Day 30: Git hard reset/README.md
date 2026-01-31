The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/apps present on Storage server in Stratos DC. This was just a test repository and one of the developers just pushed a couple of changes for testing, but now they want to clean this repository along with the commit history/work tree, so they want to point back the HEAD and the branch itself to a commit with message add data.txt file. Find below more details:

In /usr/src/kodekloudrepos/apps git repository, reset the git commit history so that there are only two commits in the commit history i.e initial commit and add data.txt file.

Also make sure to push your changes.

------------------------------------

Executing git reset --hard is the nuclear option of Git commands. It resets your working directory, staging area (index), and HEAD to a specific state, permanently deleting any uncommitted changes.

Common Commands:
  1. Discard all local changes:
  
        git reset --hard HEAD

      Wipes away every change you've made since the last commit and resets your files to that exact state.

  2. Undo the last commit and delete changes:

        git reset --hard HEAD~1

      Moves the branch back one commit and deletes the code from that "undone" commit.

  3. Match a remote branch exactly:

        git reset --hard origin/main

      Forces your local branch to match the server exactly, discarding any local commits or edits.

  4. Go to a specific point in time:

        git reset --hard <commit-hash>

      Jumps to the specific commit ID you provide


Solution:

[root@ststor01 natasha]# cd /usr/src/kodekloudrepos/apps/

[root@ststor01 apps]# git status

On branch master

Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

[root@ststor01 apps]# git log --oneline

6a9092d (HEAD -> master, origin/master) Test Commit10

0935696 Test Commit9

74c9fef Test Commit8

d3f6a75 Test Commit7

25ada89 Test Commit6

257fba2 Test Commit5

011996f Test Commit4

dd1f418 Test Commit3

acd33bd Test Commit2

adc63d6 Test Commit1

5530f5d add data.txt file

9111f91 initial commit

[root@ststor01 apps]# git reset --hard 5530f5d

HEAD is now at 5530f5d add data.txt file

[root@ststor01 apps]# git log --oneline

5530f5d (HEAD -> master) add data.txt file

9111f91 initial commit

[root@ststor01 apps]# git push origin master

To /opt/apps.git

 ! [rejected]        master -> master (non-fast-forward)
 
error: failed to push some refs to '/opt/apps.git'

hint: Updates were rejected because the tip of your current branch is behind

hint: its remote counterpart. If you want to integrate the remote changes,

hint: use 'git pull' before pushing again.

hint: See the 'Note about fast-forwards' in 'git push --help' for details.

[root@ststor01 apps]# git push origin master -f

Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)

To /opt/apps.git

 + 6a9092d...5530f5d master -> master (forced update)

