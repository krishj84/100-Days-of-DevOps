The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/beta present on Storage server in Stratos DC. One of the developers stashed some in-progress changes in this repository, but now they want to restore some of the stashed changes. Find below more details to accomplish this task:

Look for the stashed changes under /usr/src/kodekloudrepos/beta git repository, and restore the stash with stash@{1} identifier. Further, commit and push your changes to the origin.

-------------------------------

git stash is a command used to temporarily "shelve" (save) your local uncommitted changes so you can work on something else with a clean working directory, then come back and re-apply them later. 

Essential Commands

  git stash: Saves your current tracked modifications (staged and unstaged) and reverts your branch to the last commit.

  git stash pop: Re-applies the most recent stash to your current branch and removes it from your stash list.

  git stash apply: Re-applies the most recent stash but keeps it in the list for later use.

  git stash list: Shows all stashes currently stored in your "stack".

  git stash show: Displays a summary of the changes in your latest stash.

  git stash drop: Deletes the most recent stash from the list. 

Useful Options

  Stash with a message: Use git stash push -m "your message" to label your stash for easier identification later.

  Include untracked files: By default, Git only stashes tracked files. Use git stash -u (or --include-untracked) to include new files you haven't added to Git    yet.

  Include ignored files: Use git stash -a (or --all) to stash everything, including files ignored by your .gitignore.

  Stash specific files/parts: Use git stash -p (or --patch) to interactively select which "hunks" of code you want to stash.

  Apply a specific stash: Use git stash apply stash@{2} to apply a specific entry from your git stash list. 

Standard Restoration:
  
  Keep the stash: git stash apply (Recommended)

    Reapplies changes but keeps the stash in your list so you can use it again or on other branches.

  Remove after applying: git stash pop

    Reapplies changes and immediately deletes the stash from your list.

  Specific stash: If you have multiple, use git stash apply stash@{n} (where n is the index from git stash list).


Solution:

[root@ststor01 natasha]# cd /usr/src/kodekloudrepos/beta/

[root@ststor01 beta]# git status

On branch master

Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

[root@ststor01 beta]# git stash list

stash@{0}: WIP on master: a805769 initial commit

stash@{1}: WIP on master: a805769 initial commit

[root@ststor01 beta]# git stash apply stash@{1}

On branch master

Your branch is up to date with 'origin/master'.

Changes to be committed:

  (use "git restore --staged <file>..." to unstage)
  
        new file:   welcome.txt

[root@ststor01 beta]# git status

On branch master

Your branch is up to date with 'origin/master'.

Changes to be committed:

  (use "git restore --staged <file>..." to unstage)
  
        new file:   welcome.txt

[root@ststor01 beta]# ls

info.txt  welcome.txt

[root@ststor01 beta]# git add --all

[root@ststor01 beta]# git commit -m "Added new file welcome.txt"

[master fb75a5b] Added new file welcome.txt

 1 file changed, 1 insertion(+)
 
 create mode 100644 welcome.txt
 
[root@ststor01 beta]# git push origin master

Enumerating objects: 4, done.

Counting objects: 100% (4/4), done.

Delta compression using up to 16 threads

Compressing objects: 100% (2/2), done.

Writing objects: 100% (3/3), 311 bytes | 311.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)

To /opt/beta.git

   a805769..fb75a5b  master -> master
