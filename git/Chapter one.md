
What Is Git?
Git is a technology that can be used to track changes to a project and to help
multiple people to collaborate on a project. At a basic level, a project version
controlled by Git consists of a folder with files in it, and Git tracks the changes
that are made to the files in the project. This allows you to save different
versions of the work you’re doing, which is why we call Git a version control
system.


git commit -m "<message>"
-m -> option 
<message> -> argument 
options are denoted by - or --

pwd - print working directory

Commands
git config --global  --list : list the variables in the global git configuration file and their values
it will show information of the global git configuration file -> usually .gitconfig file

![[image1.png]]

Variables we are interested in are: user.email and user.name. Every time someone saves a version of their project(i.e commits), Git will note down the name and email address of the individual and associate it with that saved version.The user.name and user.email variables
are used to set the name and email address that will be saved for the commits
you make. This means that you can see who worked on what in a Git project.

To set these variables in your global Git configuration file, you pass them as
arguments to the git config command, entering your desired values inside
quotation marks.

![[image2.png]]

Text editor - Program that allows a user to edit plain text.
Some advanced text editors like VS Code ~ IDEs (Integrated Development Environment) come with integrated terminal, in which you can execute the commands you would normally use in your command line window.

