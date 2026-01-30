The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/blog present on Storage server in Stratos DC. However, they reported an issue with the recent commits being pushed to this repo. They have asked the DevOps team to revert repo HEAD to last commit. Below are more details about the task:

In /usr/src/kodekloudrepos/blog git repository, revert the latest commit ( HEAD ) to the previous commit (JFYI the previous commit hash should be with initial commit message ).

Use revert blog message (please use all small letters for commit message) for the new revert commit.

Solution:
[root@ststor01 blog]# git status

On branch master

Your branch is up to date with 'origin/master'.

Untracked files:

  (use "git add <file>..." to include in what will be committed)
  
        blog.txt

nothing added to commit but untracked files present (use "git add" to track)

[root@ststor01 blog]# git log --oneline

8ab797a (HEAD -> master, origin/master) add data.txt file

2fe9243 initial commit

<img width="1506" height="810" alt="image" src="https://github.com/user-attachments/assets/0578de6f-ef9e-4bcd-a701-19eae9c2fe8b" />

[root@ststor01 blog]# git revert HEAD

[master 61a9b53] revert blog Revert "add data.txt file"

 1 file changed, 1 insertion(+)
 
 create mode 100644 info.txt
 
[root@ststor01 blog]# git log --oneline

61a9b53 (HEAD -> master) revert blog Revert "add data.txt file"

8ab797a (origin/master) add data.txt file

2fe9243 initial commit

[root@ststor01 blog]# 

