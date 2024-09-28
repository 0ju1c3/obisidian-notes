
![[Pasted image 20240710001858.png]]

If I follow the parent links of the main branch backward, I can see that the
branch is made up of commits A and B. In other words, the development
history of the main branch consists of commits A and B. On the other hand,
the development history of the chapter_six branch consists of commits A,
B, C, D, and E.
If we can reach one branch through the commit history of another branch, we
say that the development histories of the branches have not diverged. If I
follow the parent links from the chapter_six branch, which points to
commit E, backward, I reach the main branch, which points to commit B.
Therefore, the main branch and the chapter_six branch have not diverged.
If I were to now merge the chapter_six branch into the main branch, a fast-
forward merge would occur. During the fast-forward merge, the main branch
pointer would move forward to point to the commit that the chapter_six branch points to, which is commit E


![[Pasted image 20240710001945.png]]

chapter_six is the source branch and main is the
target branch. Figure 5-3 shows that the main branch pointer simply moved
forward from commit B to commit E. This is why these kinds of merges are
called “fast-forward” merges.

a three-way merge is a type of
merge that occurs when the development histories of the branches involved in
the merge have diverged. Development histories have diverged when it is not
possible to reach the target branch by following the commit history of the source
branch. In this case when you merge the source branch into the target branch, Git
performs a three-way merge, creating a merge commit to tie the two
development histories together; it then moves the pointer of the target branch to
the merge commit.

![[Pasted image 20240710190611.png]]

In Figure 5-5, you can see that the development history of the
chapter_eight branch is made up of commits F, G, H, I, and J. On the other
hand, the commit history of the main branch is made up of commits F, G, K,
and L. There is no way to follow the parent links (represented by gray
arrows) of the chapter_eight branch backward to reach the commit that the
main branch points to, which is commit L. In Git, to describe this situation,
we say that the development histories of the branches have diverged.

If I merge the chapter_eight branch into the main branch, it can’t be a fast-
F I G U R E 5 - 4
The commit history of the book repository with the last two commits on the main branch
F I G U R E 5 - 5
An example of a commit history where work has been added to the main branch and the
chapter_eight branch
forward merge because there is no way to just move the branch pointer
forward to combine these two development histories. Instead, a merge
commit (represented by commit M) will be created to tie the two
development histories together, as shown in Figure 5-6. A merge commit is a
commit that has more than one parent. This is an example of a three-way
merge

![[Pasted image 20240710191000.png]]

In Figure 5-6, commit M points back to both commit J and commit L. The
reason that this kind of merge is called a three-way merge is because in order
to carry out the merge, Git will take a look at the two commits that the
branches involved in the merge are pointing to—in the case of the book
repository, commit J and commit L—as well as the commit that is the
common ancestor of these two commits, which in this case is commit G.
Hence the name, “three-way” merge

Three-way merges are a more complex type of merge where you may experience
merge conflicts. These arise when you merge two branches where different
changes have been made to the same parts of the same file(s), or if in one branch
a file was deleted that was edited in the other branch


![[Pasted image 20240710191415.png]]


![[Pasted image 20240710191636.png]]

If Git detects that switching branches will cause you to lose uncommitted
changes in your working directory, then it will stop you from switching branches
and present you with an error message. However, this happens only if the files
that contain uncommitted changes have conflicting changes in the branch you
are switching onto

Suppose I want to work on two different approaches for chapter 5 in my book
repository. This means I’ll be working on the chapter_five.txt file. I make
two branches off the main branch, once called chapter_five_approach_a
and one called chapter_five_approach_b.
First I go onto the chapter_five_approach_a branch and work on approach
A. I make a couple commits. In these commits I’m editing the
chapter_five.txt file.
Next, I decide to switch onto the chapter_five_approach_b branch to work
on approach B in my text editor. While on the chapter_five_approach_b
branch, I edit the chapter_five.txt file extensively, but I forget to actually
make any commits on the branch (in other words, to properly save my work).
At some point, I decide I want to switch back to thechapter_five_approach_a branch to check something I had done on that
branch. If Git simply allowed me to switch branches, then the version of the
chapter_five.txt file in my working directory that I was working on in the
chapter_five_approach_b branch would be replaced by the version of the
file in the chapter_five_approach_a branch, and I would lose all my
changes that I had worked on in approach B because I forgot to commit
them.
Luckily, Git won’t let this happen. Instead, it will warn me that I have
uncommitted changes and it will remind me to make a commit so I won’t
lose them.

Git will not prevent you from switching branches if you make changes to files without saving
them in the text editor, because those files will be considered unmodified files. So, always
remember to save files in your text editor when you’re done working on them!

![[Pasted image 20240710193203.png]]


![[Pasted image 20240710193224.png]]

You have just explicitly observed that switching branches changes the contents
of the working directory

 I mentioned that the git log command shows a list of commits in reverse chronological order. However, in reality, it shows only a list of commits that are reachable by following the parent links from the commit you are on when you execute the command. To see a list
of commits for all the branches in your local repository, you must use the git log command with the --all option.

![[Pasted image 20240710193423.png]]

![[Pasted image 20240710193701.png]]

I mentioned that the git checkout command may be used to
switch branches as well as to carry out other actions. One of the other things you
can do with the git checkout command is check out commits.
At the moment, you are on the main branch, which points to the yellow commit.
But what if you want to look at an older version of your project? For example,
what if you want to see the state of your project at the orange commit?
There is currently no branch pointing to the orange commit, so you can’t switch
onto it by switching onto a branch. Instead, you can choose to check out that
commit by using the git checkout command and passing in the commit hash of
the orange commit

![[Pasted image 20240710194107.png]]

When you do this, the git checkout command will carry out three actions that
are similar to the ones described in Chapter 4 and earlier in this chapter:
1. It changes the HEAD pointer to point to the commit you are switching onto.
2. It populates the staging area with all the files and directories that are part of
the commit you are switching onto.
3. It copies the contents of the staging area into the working directory.
The main difference between these steps and the steps mentioned previously is
that in step 1 the HEAD pointer will point directly to a commit instead of pointing
to a branch. This means that you will be in something that Git (scarily) calls
detached HEAD state. This allows you to look at any commit—or, in other
words, any version of your project—in your entire repository.
As these steps indicate, checking out commits changes the contents of the
working directory in the same way that switching branches does.

![[commitCheckout.png]]



![[createBranch.png]]
