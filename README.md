# GitHub Tutorial

_by Alan Po_

---
## Git vs. GitHub
Github is a code storing platform for version control and collaboration, but it requires git.
In addition, git is a version control system that manage a project and its files inside of a repository(a system or directory that stores multiple versions of files), but it doesn't require github.


---
## Initial Setup
#### The Importance of SSH Key
SSH key is an alternate way to identify yourself without entering your password and username. SSH is important because we often work with github repository and we have to identify ourselves by entering our username and password; however, we can authenticate the remote and user by using SSH key which is more convenient.
####  before Inital Setup:
* create an account
* enter your username and password for your accout
---
1. type the following: git config --global user.email "you@example.com"
2. git config --global user.name "Your Name"
* Make sure you are in the root directory by doing cd
3. ssh-keygen -t rsa -b 4096 -C "you@example.com" then slowly press ENTER repeatedly until you see something likeThe key's randomart image.
4. eval "$(ssh-agent -s)" starts the agent in the background
5. ls -al ~/.ssh you should now see a file named id_rsa.pub
6. cat ~/.ssh/id_rsa.pub then copy all of the result to your clipboard (it should start with ssh-rsa and end with your email address)
7. Go to [https://github.com/settings/keys](https://github.com/settings/keys) > New SSH Key
  * Title: ide50
  * Key: paste your ssh key
  * Press the green Add SSH key button
8. Back in your cs50 IDE, do sudo nano ~/.ssh/config
9. Paste the following:
Host github.com
Hostname ssh.github.com
Port 443
10. control+X to exit, then press Y then ENTER
11. ssh -T git@github.com
12. Type yes, press ENTER, and you should see
`Hi "username"! You've successfully authenticated, but GitHub does not provide shell access.`

Here is the link ["Tutorial of the Full Github Setup"](https://github.com/hstatsep/ide50)


---
## Repository Setup
1. create a new directory using `mkdir`
2. move into the directory using `cd` and initialize the directory using `git init`
3. after you finish making edits in your repository, you add the files on the stage using `git add`
4. after you add the files on the stage, you commit the files using `git commit -m`
5. therefore you should create a new repository on github
6. In order to setup the repository, you link the remote and local together. You copy and paste the two link that say "push an existing repository from the command line"
7. At the end, you push the commits to your remote using `git push -u origin master`

---
## Workflow & Commands
* git init = initializes git in your directory into repository for version control
* git status = see which files have been edited since the last commit
* git add (file's name) = add the files on the stage to be committed
* git commit -m "a message" = commit all the files on the stage
* git push = upload current local repository to the remote repository, including all of your commits and edits


---
## Rolling Back Changes
#### undo commit
* git revert (a commit message) = revert back to the commit where you want
1. type `git log` to see all the commits
2. choose the commit that you want to revert and copy the SHA(unqiue commit IDs)
3. use git revert (SHA) or git revert head(this can bring you back to your latest commit.)  
4. press q to quit `git log` if you don't want any changes

#### undo edit 
1. type `git status`
2. In order to undo any edits you've done since your latest commit, you have to type `git checkout` and the file's name.

#### undo add 
1. type `git status`
2. In order to undo "add"ing to the stage, you have to type `git reset` and the file's name. 

#### undo push 
