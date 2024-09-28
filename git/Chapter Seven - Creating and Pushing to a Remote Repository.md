
STARTING FROM A LOCAL REPOSITORY
To start to work on a Git project from a local repository, you must first create a
local repository on a computer using the git init command and make at least
one commit. Next, you must create a remote repository on a hosting service.
Finally, you may upload data from the local repository to the remote repository.
In Git, we use the term push or pushing to refer to the process of uploading data
from a local repository to a remote repository, and the command we use to do
this is git push.

![[Pasted image 20240712151008.png]]

Local repositories and remote repositories act separately. When it comes to
working with them, it’s important to understand that no interaction between them
happens automatically. In other words, no updates from the local repository to
the remote repository will happen automatically, and conversely, no updates
from the remote repository to the local repository will happen automatically.
There is no live connection between the two. Any changes in either will be the
result of you explicitly executing commands. In this and the following chapters,
you will learn what these commands are

Why Do We Use Remote Repositories?
There are three main reasons why remote repositories are useful and important
when working on a Git project. They allow you to:
• Easily back up your project somewhere other than your computer.
• Access a Git project from multiple computers.
• Collaborate with others on Git projects.

If a local repository was initialized locally, to set up a connection to a remote
repository you must explicitly associate the remote repository URL to the remote
repository shortname. To do this you use the git remote add command, passing
in the shortname followed by the remote repository URL.

![[Pasted image 20240712171215.png]]

![[Pasted image 20240712171307.png]]

In the official Git documentation, a connection to a remote repository stored in a local
repository is simply referred to as a remote

To see the list of connections to remote repositories stored in a local repository
by shortname, you may use the git remote command. If you pass in the -v
option (which stands for “verbose”) to the git remote command, then it lists the
connections to remote repositories stored in a local repository by shortname
along with their URLs.

![[Pasted image 20240712171545.png]]

![[Pasted image 20240712171658.png]]

![[Pasted image 20240712184557.png]]

• The rainbow repository has a shortname associated with the remote
repository URL, called origin.
• The rainbow-remote repository still does not have any data in it.

You can see that the arrow that represents the shortname
stored in the rainbow repository that relates to the rainbow-remote repository is
going in only one direction. This is because the connection between a local and a
remote repository goes from the local repository to the remote repository but not
the other way around. In a local repository, you can find a list of all the remote
repositories it has stored a connection to; however, in a remote repository you
cannot find a list of local repositories that store a connection to that remote
repository.


Notice as well that just because you added a connection to the remote repository
in your local repository does not mean that any data from the local repository
was uploaded to the remote repository. To upload data to a remote repository,
you must push a branch to the remote repository. This process will upload all the
commits that are part of that branch

In Chapter 4 you learned about branches, which as you saw are movable pointers
to commits. Up until now, you have worked only with local branches. When you
push a local branch to a remote repository, you will create a remote branch. A
remote branch is a branch in a remote repository.

Remote branches do not automatically update when you make more commits on
local branches. You have to explicitly push commits from a local branch to a
remote branch. Every remote branch (that a local repository knows about) also
has a remote-tracking branch. This is a reference in a local repository to the
commit a remote branch pointed at the last time any network communication
happened with the remote repository. You can think of it as being like a
bookmark

You can set up a tracking relationship between a local branch and a remote
branch by defining which remote branch a local branch should track. This is
referred to as the upstream branch. There are some cases where Git will set the
upstream branch automatically, but in other cases you have to set it explicitly.

When you push work from a local branch to a remote branch, Git needs to know
which remote branch you want to push to. If the local branch has an upstream
branch defined for it, you can use git push with no arguments, and Git will
automatically push the work to that branch. However, if no upstream branch is
defined for the local branch you’re working on, you’ll need to specify which
remote branch to push to when you enter the git push command

To push a local branch to your remote repository, you will use the git push
command and pass in the shortname for the remote repository and the name of
the branch that you want to push. For the rainbow repository, the shortname you
will use is origin and the branch you will push is main.

![[Pasted image 20240712185501.png]]

After you execute the git push command, two things will happen:
1. A remote branch will be created in your remote repository.
2. A remote-tracking branch will be created in your local repository

To push data to a remote repository, you must be connected to the internet and have either
SSH access or HTTPS access to your hosting service of choice.

![[Pasted image 20240712185757.png]]

![[Pasted image 20240712190519.png]]

![[Pasted image 20240712190538.png]]

4