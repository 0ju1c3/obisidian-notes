**COMMIT EARLY, COMMIT OFTEN**

**git status** - Tells you the state of the working directory and the staging area, this is useful because in a project with many files it is easy to lose track of what state the files in your working directory are in and which files you've added to the staging area.

In a project with many files, it can be hard to remember which files are untracked, which files are tracked, and which files you’ve edited. 

Example Book Project 3-1
The Book project I’m working on consists of 10 files, one for each chapter in the book. After working on the book for a while in between commits, I may forget which chapter files I have edited. I know I worked on chapters 2 and 3, but did I make any changes in chapter 4? If so, I don’t want to lose them.
In this case, the git status command can help me by telling me which
chapter files I’ve edited, which ones I’ve added to the staging area, and which ones I have yet to add.

![[Pasted image 20240610222102.png]]



![[Pasted image 20240610222148.png]]
							*rainbow project*

** No commits yet- The commit history doesn't have any commits at this point of time.


![[Pasted image 20240610222416.png]]

The staging area allows you to choose which updated files (or changes) will be included in your next commit. The general rule is to group related changes together. This allows you to keep your commits more organized.

This first step of the committing process allows you to be very specific about what you include in a commit. This means that you can edit many files in your project, but you don’t have to save them all in one commit.

In the Rainbow project, the rainbowcolors.txt file is the first file you will add
to the staging area. This means that when you add this file, the index file (which
represents the staging area in the .git directory) will be created. As you learned
in Chapter 2, this file does not exist until you add a file to the staging area.The
index file is a binary file, which means the actual contents look like gibberish to
a human and are not easily understandable. For our purposes, we only need to
understand that it represents the staging area.

![[Pasted image 20240610230007.png]]

![[Pasted image 20240610230047.png]]

The rainbowcolors.txt file is now both in the working directory and in the
staging area. This is because the git add command does not move a file from
the working directory to the staging area. It copies the file from the working
directory into the staging area.

![[Pasted image 20240610230131.png]]

**Upon running git add rainbowcolours.txt git commit -m "Red"**
![[Pasted image 20240610230458.png]]

The output of the git commit command shows the first seven characters of
the commit hash for the red commit, which is c26d0bc in this book. The
first seven characters of your commit hash will be different.

![[Pasted image 20240610230557.png]]

Viewing a List of Commits
To see a list of commits in the commit history, you use the git log command.
The **git log** command lists the commits in a local repository in reverse
chronological order. It displays four pieces of information about each commit:
1. Commit hash
2. Author name and email address
3. Date and time commit was made
4. Commit message

![[Pasted image 20240610230812.png]]

