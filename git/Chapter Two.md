
Repository/ repo is how we refer to a project version controlled by GIt.
Two types of repos:
	-Local repo: Stored on a computer
	-Remote repo: Hosted on a hosting service

*Hosting service: Companies that provide hosting for projects using Git. Eg: GitHub, GitLab, BitBucket*

A local repository is represented by a hidden directory called .git that exists
within a project directory. It contains all the data on the changes that have been
made to the files in a project.
To turn a project directory into a local repository you have to initialize, or create,
the repository. When you initialize a repository, the .git directory is
automatically created inside the project directory. Because the .git directory is a
hidden directory, you won’t be able to see it unless you explicitly make hidden
files and directories visible.

Normally we initialize a Git repo using **git init** command, with no additional options; however, in the rainbow project(/dev/oreilly/learning-git/rainbow), we wil use  git init -b where -b stands for --initiali-branch and pass in the name main(argument).

Hence, **git init -b main**

By default Git will create a branch called master when you initialize a new
local repository. From Git version 2.28 onwards, the name of the initial branch is
configurable. I have chosen to use the name main instead of master in this book,
because “master” is not considered inclusive terminology.

![[image3.png]]

**Running the command: git init -b main*** in the rainbow repo*

![[image4.png]]
*The contents of .git repo right after running **git init** command*

Four important areas to be aware of when working with Git:
	- Working directory
	- Staging area
	-  Commit History
	-  Local repository

	Introduction to Working Directory:
		The working directory contains the files and directories in the project directorythat represent one version of a project. It is sort of like a workbench. It is where you add, edit, and delete files and directories.

		![[workingDirectory.png]]
		

	Introduction to the Staging Area:
		The staging area is similar to a rough draft space. It is where you can add and remove files, when you are preparing what you want to include in the next saved version of your project (your next commit). The staging area is represented by a file in the .git directory called index.

		![[stagingArea.png]]
		

	What is a Commit ?
		A Commit in Git is basically one version of a project.
		Every commit has a commit hash (sometimes called a commit ID). This is a unique 40-character hash composed of letters and numbers that acts like a name for the commit, providing a way to refer to it. An example of a commit hash is 51dc6ecb327578cca503abba4a56e8c18f3835e1. In reality, you only need the first seven characters of a commit hash to refer to a commit. So, for the example hash just given, you can just use 51dc6ec to refer to the commit.

	Introducing the Commit History
		The commit history is where you can think of your commits existing. It is represented by the objects directory inside the .git directory.

		![[commitHistory.png]]



![[rainbowColors.png]]

Since the rainbowcolors.txt file is not yet in your repository, it is an untracked
file. An untracked file is a file in the working directory that Git is not version
controlling. It has never been added to the staging area and it has never been
included in a commit; therefore, it is not part of the repository.
Once you add a file to the staging area and include it in a commit, the file
becomes a tracked file. This is a file that is version controlled (in other words, a
file that Git tracks).
Every new file in a project version controlled by Git needs to be explicitly added
to the staging area and then included in a commit in order to become a tracked
file.