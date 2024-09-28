Why Do We Use Branches?
Before we get into the specifics of branches in Git, I want to explain why they’re
so useful. There are two main reasons to use branches:
• To work on the same project in different ways.
• To help multiple people work on the same project at the same time.

One common pattern for working with branches is to have one official primary
line of development—the main or primary branch—and off of that to create
secondary branches, called topic branches or feature branches, that are used to
work on just a specific part of the project. These topic branches are short-lived;
they are ultimately combined or incorporated back into the primary branch and
then deleted. The two processes you can use to integrate one branch into another
are called merging and rebasing.


In the git log output, next to the commit hash inside the parentheses you
see HEAD -> main.
The branch or branches that appear inside the parentheses next to a particular
commit hash in the git log output are the branches that point to that commit.

Within the rainbow project directory in your filesystem window, go to .git > refs >
heads > main

Inside the main file you will see the commit hash for the red
commit in your rainbow repository

refs stand for references

The heads directory stores a file for each local
branch in your local repository. At the moment you only have one local branch,
the main branch, so there is only one file in this directory. You can think of that
file as storing the “head” of that branch; in other words, the latest commit on that
branch.

Git
knows about the rainbowcolors.txt file because it has been included in a
commit, and therefore it is a tracked file

Tracked files in the working directory can be in one of two states. Unmodified
files are files in the working directory that have not been edited since the last
commit. Once a file in the working directory has been edited (and saved in the
text editor), it becomes a modified file. Since your last commit, you have not
edited the rainbowcolors.txt file; therefore, it is an unmodified file.


![[Pasted image 20240612203517.png]]

*In the Visualize It diagrams, gray arrows are used to represent parent links and black
arrows are used to represent branch pointers.*

second commit "orange", main points to orange, which points to red

To check which commit is the parent of a given commit, you can use the git
cat-file command with the -p option and pass in a commit hash: **git cat-**
**file -p <commit_hash>.**

![[Pasted image 20240612203810.png]]

In the git cat-file -p output, you can see that next to parent it
references the commit hash of the red commit in this book. In your output,
it will reference the commit hash of your red commit

![[Pasted image 20240612203908.png]]

![[Pasted image 20240612204054.png]]


A new branch willinitially point to the commit that you were on when you made the branch. In this case, you can say that you “made the feature branch off of the main branch.”
That is why the feature branch and main branch both now point to the same
commit.

**WHAT IS HEAD?**
At any given point in time, you are looking at a particular version of your
project. Therefore, you are on a particular branch which is pointing to a commit.
HEAD is simply a pointer that tells you which branch you are on.

![[Pasted image 20240612204321.png]]

![[Pasted image 20240612204333.png]]

HEAD (in capital letters) should not be confused with the heads directory that can be found in .git > refs > heads. The heads directory stores a file for every local branch in your local
repository, while HEAD indicates which branch you are on by referencing one of the files
inside the heads directory. You can distinguish them because HEAD is always in capital letters.

To work on another branch (or line of development) in a Git project, you have to
switch onto that branch. Another way of saying this in Git terminology is that
you have to “check out” another branch.
You currently have two branches, main and feature. But as you’ve just seen,
just because you make a branch in Git does not mean that you automatically
switch onto that branch. You must explicitly instruct Git that you want to switch
onto a branch. You can do this using either the git switch command or the git
checkout command, passing in the name of the branch that you want to switch
onto.

![[Pasted image 20240612204523.png]]

The git switch (or git checkout) command does three things when used to
switch branches:
1. It changes the HEAD pointer to point to the branch you are switching onto.
2. It populates the staging area with a snapshot of the commit you are
switching onto.
3. It copies the contents of the staging area into the working directory.

Upon doing,
git switch feature 
![[Pasted image 20240612204945.png]]

HEAD now points towards the feature branch : can check through .git/HEAD

![[Pasted image 20240612205131.png]]
*Commiting Yellow on branch feature*

![[Pasted image 20240612205217.png]]

