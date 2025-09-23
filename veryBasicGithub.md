# Very Basic Github

This is the simplest possible cheat sheet to use github.

## Creating a git account

* Open a browser and go to [https://github.com/](https://github.com/)
* click on `sign up` and create a personal github account (choose a username which you are happy to live with)
* use your personal email and not you university email when signing up.

## Forking a repository

Forking a repository means creating a copy of it in your own github account.
You cannot modify the `upstream` repository but you can checkout and modify your own repository.

* Log into your own github account.
* Navigate in your browser to the repository you want to fork (i.e. this `https://github.com/gallenc/COM304_FOUNDATION_1/`  repository)
* Select `Fork` to clone this repository into your own account
     ![alt text](../main/docs/images/ForkingARepo.png "Figure ForkingARepo.png")

You should now have a duplicate copy of the repository in your own account.

## Creating an access token

You will need a personal access token to use when you are pushing code to your account.
(A better more secure alternative is to use SSH keys but access tokens will work OK).

* Sign into github usng your new account
* Select your account icon on the top right of your github page and select `Settings`
    ![alt text](../main/docs/images/githubsettings1.png "Figure githubsettings1.png")
* On the personal settings page open `developer settings`
     ![alt text](../main/docs/images/githubsettings2.png "Figure githubsettings2.png")
* Under developer settings select Personal Access Tokens / Tokens (Classic) / Generate New Token (Classic)
    ![alt text](../main/docs/images/githubsettings3.png "Figure githubsettings3.png")
* Under the New personal Access token (classic) add a note (which tells you what this token is for).
* Select 90 days for the life of the token. After 90 days you will need to generate a new token.
* Select `repo` full control of private repositories. ( do not select other permissions)
* select `Generate token`
    ![alt text](../main/docs/images/githubsettings4.png "Figure githubsettings4.png")
* The token will be generated and will only be visible once. Copy the token to a safe place. Treat it like a password.
    ![alt text](../main/docs/images/githubsettings5.png "Figure githubsettings5.png")


## Installing Git on your PC

If you have a windows PC, download and install GIT For Windows from [https://git-scm.com/downloads/win](https://git-scm.com/downloads/win)

The class is designed around Windows so we can't provide full support or help with Macs. 
However if you have an Apple Mac download and install GIT for Mac from 
* [https://git-scm.com/downloads/mac](https://git-scm.com/downloads/mac)
* Additional MAC Git installation instructions are also be found here [https://www.atlassian.com/git/tutorials/install-git](https://www.atlassian.com/git/tutorials/install-git)

Git is installed in the classroom PC's

## Cloning your repository

Having installed Git, we are now in a position to clone the remote Git repository onto your local PC. 
Cloning means creating a complete local copy of the remote git repository including all of the change records.

First we need to create a directory where we want to store our repository clones.
This needs to be as close to the `root` of the drive as possible and the path to your repository must not have any spaces in the directory names.
You should also not use a directory which is backed up with `one drive` or any other network drive as this can cause real problems for Git.

* Open a `Windows Explorer` and in the top panel type `C:`
* Right Click inside the explorer and create a new folder `C:\gitrepos`
    ![alt text](../main/docs/images/checkoutGit2.png "Figure gcheckoutGit2.png")
* Inside `Windows Explorer`, Right click on the `C:\gitrepos` folder and select `git bash` to open a git window inside the folder.
* Alternatively - on the class PC's, Use the windows search bar to open a `git bash` terminal. Inside the terminal type `cd C:\gitrepos`

Now we can clone our repo into the folder.

* In your own repository fork, select `code / HTTPS` and copy the `https://github.com/your-username/repository` url.
    ![alt text](../main/docs/images/githubsettings6.png "Figure githubsettings6.png")
* To clone your repository, in the git bash window type `git clone -your-url-`
    ![alt text](../main/docs/images/checkoutGit1.png "Figure checkoutGit1.png")

## Making changes locally and pushing to github

Now that you have downloaded your repository on your local machine you can make changes and push them back up to your main repo.

* Edit a file in your cloned repository using the windows notepad text editor. Make a local small change and save the file.
    ![alt text](../main/docs/images/editFile.png "Figure editFile.png")
* In the git terminal, commit and push your changes
    ![alt text](../main/docs/images/checkoutGit3.png "Figure checkoutGit3.png")

The general commands for committing code are

```
# git pull retrieves any changes from the upstream repository into your repo
git pull 

# git status tells you if you have changes to commit or push
git status

# git add --all adds any changed files to the `index` which will be committed
git add --all

# git commit saves all of your current changes in your local repository.
# it is usual to add a meaningful message to the commit
git commit -m 'a meaningful message for this commit'

# git push pushes the current repo to your foreign repo. Note you must have pulled any foreign changes 
# and merged them with yours first.
git push

# (you will be asked to enter your access token generated earlier)

```

