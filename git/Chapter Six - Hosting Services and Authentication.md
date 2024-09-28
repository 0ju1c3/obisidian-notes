

 two types of repositories: local repositories and remote
repositories. Local repositories are found on a computer, while remote
repositories are hosted on a hosting service in the cloud.

To transfer data between a local repository and a remote repository on a hosting
service, you must connect and authenticate using either SSH or HTTPS

The HTTPS protocol uses a username and some sort of password (or
authentication credential) to allow you to securely connect to remote
repositories. In the past, all the hosting services allowed you to use the password
you use to log in to your account on the hosting service (which we will refer to
as the account password) for HTTPS authentication as well. However, GitHub
and Bitbucket no longer allow this; they require you to create another
authentication credential.
In GitHub, the authentication credential is called a personal access token. In
Bitbucket, it’s called an app password. With GitLab, you can still simply use
your account password to authenticate. See Table 6-1 for an overview of the
three most common hosting services and the access credentials necessary to
authenticate over HTTPS

Setting up HTTPS: https://github.com/gitlearningjourney/learning-git

USING SSH
The SSH protocol uses a public and private SSH key pair to allow you to
securely connect to remote repositories. The three main steps to setting up SSH
access are:
1. Create an SSH key pair on your computer.
2. Add the private SSH key to the SSH agent.
3. Add the public SSH key to the hosting service account.

Setting up SSH: https://github.com/gitlearningjourney/learning-git


