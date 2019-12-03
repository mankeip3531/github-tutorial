# GitHub Tutorial

_by Alan Po_

---
## Git vs. GitHub
Github is a code storing platform for version control and collaboration, but it requires git.
In addition, git is a version control system that manage a project and its files inside of a repository(a system or directory that stores multiple versions of files), but it doesn't require github.


---
## Initial Setup
#### The Importance of SSH Key
**SSH key** is an alternate way to identify yourself without entering your password and username. SSH is important because we often work with github repository and we have to identify ourselves by entering our username and password; however, we can authenticate the remote and user by using SSH key which is more convenient.
####  before Inital Setup:
* Create an account
* Enter your username and password for your accout
---
1. In your command line, type the following: `git config --global user.email "you@example.com"`
    * Don't copy/paste.
    * Remember to use YOUR email address.
    * YES, you need the quotes.
    * Example: `git config --global user.email "johnd1234@hstat.org"`
2. Then type `git config --global user.name "Your Name"`
    * Example: `git config --global user.name "John Doe"`
* Make sure you are in the root directory by doing cd
3. `ssh-keygen -t rsa -b 4096 -C "you@example.com"` then slowly press `ENTER` repeatedly until you see something like:
The key's randomart image is:
```
+--[ RSA 4096]----+
|       .o o..    |
|       o +Eo     |
|        + .      |
|         . + o   |
|        S o = * o|
|           . o @.|
|            . = o|
|           . o   |
|            o.   |
+-----------------+
```
4. `eval "$(ssh-agent -s)"` starts the agent in the background
5. `ls -al ~/.ssh` you should now see a file named id_rsa.pub
6. `cat ~/.ssh/id_rsa.pub` then copy all of the result to your clipboard (it should start with `ssh-rsa` and end with your email address)
7. Go to [https://github.com/settings/keys](https://github.com/settings/keys) > New SSH Key
  * Title: ide50
  * Key: paste your ssh key
  * Press the green Add SSH key button
8. Back in your cs50 IDE, do sudo nano `~/.ssh/config`
  * Example: git config --global user.name "John Doe"
9. Paste the following:
```
Host github.com
Hostname ssh.github.com
Port 443
```
10. `control+X` to exit, then press `Y` then ENTER
11. `ssh -T git@github.com`
12. Type `yes`, press `ENTER`, and you should see
`Hi "username"! You've successfully authenticated, but GitHub does not provide shell access.`

Here is the link ["Tutorial of the Full Github Setup"](https://github.com/hstatsep/ide50)


---
## Repository Setup
1. Create a new directory using `mkdir`
2. Move into the directory using `cd` and initialize the directory using `git init`
3. After you finish making edits in your repository, you add the files on the stage using `git add`
4. After you add the files on the stage, you commit the files using `git commit -m`
5. Therefore you should create a new repository on github
6. In order to setup the repository, you link the remote and local together. You copy and paste the two link that say "push an existing repository from the command line"
7. At the end, you push the commits to your remote using `git push -u origin master`

---
## Workflow & Commands
* `git init` = initializes git in your directory into repository for version control
* `git status` = see which files have been edited since the last commit
* `git add` (file's name) = add the files on the stage to be committed
* `git commit` -m "a message" = commit all the files on the stage
* `git push` = upload current local repository to the remote repository, including all of your commits and edits


---
## Rolling Back Changes
#### undo commit to add
* `git reset` --soft HEAD~1

#### undo commit to edit
* `git reset` HEAD~1
#### undo edit (revert your files back to your last commit)
* `git checkout` -- filename


#### undo add (unstage your files)
* `git reset` HEAD filename

#### undo push
* `git reset` --hard HEAD~1

---
## error handling
* if you did init in the wrong directory, you type in `rm -rf .git` to remove the repository
* In order to remove a repository or directory completely, you use `rm -rf (directory's name)`

