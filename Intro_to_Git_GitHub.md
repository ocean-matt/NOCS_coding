# Introduction to Git and GitHub

Git and GitHub are both free and useful code tracking packages. 
This file aims to clear up the differences between these similar-sounding services and introduces some of the basics.
I am happy to go through any of this with people if they want :) Matt.

## Starting comments
### *So what's the difference?*
- **Git** is a version control code management software used locally (on your personal machine) through the command prompt. 
- **GitHub** is an online hosting service for Git repositories (repos). These repos can be public or private.
- So in short, Git is a local software that can help track code versions. It can be used in conjunction with GitHub (changes made locally can be "pushed" to the remote GitHub repository).

### *Do I need to use both?*
Not nessecarily, but I would recommend using both together. 
Whilst Git is great for tracking versions of code, all code is still stored on the computer.
You could consider GitHub to be a useful online backup tool. 

### *Ok, I'm interested. How do I install it?*
First step, install Git on whatever system you are using. For Windows, this is Git Bash. 
I don't have the time or knowledge about installing on other systems, so please refer to your favorite search engine for instructions on your device.

**PLEASE NOTE:** if using the NOCS Linux systems, other NOC/NERC computing facilities (including the JASMIN supercomputer), it *should* already be installed. Try typing `module load git`.

GitHub is an online tool, so no separate installation is nessesary (although they do have their own GUI for Windows and Mac, which is completely optional and I'm not covering that here).
To use GitHub, you must register (this is free). 

Once installed, Git is relitively quick and simple to learn (see next section)


## Using Git: an example
Say I had a folder on my computer where all my files for a significant portion of my PhD are in. 
For this example, let's say the folder pathway is "home/users/matt/PhD".
* To use Git, we need to initialise this as a repository. Make sure you are in the directory before using the command `git init` 
* After making changes to files, each individual file must be added to Git tracking. Use the command `git add <filename>` or `git add *` for mulitple files.
* At any stage, use `git status` to see what files Git is tracking. You should do this to make sure all files you want tracking are being tracked BEFORE committing the changes.
* Finally, to store changes, use the command `git commit -m "<describe your changes here>"`


*These instructions have been written and tested by me on Windows and Linux systems. I cannot guarentee these will work on all systems.*

I strongly advise checking out this website, which has a simple summary table of the key Git commands: https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html


## Connecting a Git repository to GitHub using HTTPS connection
Assuming you have a Git tracked repository, you can add this to GitHub with very little faff. 
* On GitHub, create a new BLANK repository. **DO NOT** tick the boxes to automatically create README, LICENCE or other files. For this example, let's say I've named it "myrepo". GitHub will tell you the URL address of your repo. Copy this address. 
* Back to your command line, make sure you are in your local repo. 
* In the command line, type `git remote add origin <remote repository URL>`
* To verify this worked, try `git remote -v`. It should come up with the URL you just added.

To have your file changes appear on GitHub, use the same instructions for "Using Git" but with one extra line of code:
`git push origin master`. Change `master` for whatever branch you are using.


## Branches
Branches are a useful way to keep "clean" and "working" copies of code separated. 

An example use would be something like this: I have a working piece of code called "currents.m" but I am trying to add some new features to it which may cause the working code to no longer work.
One way to get round this using Git is to use a new branch. The default branch is called "master" and will be present in every Git/GitHub repo. Creating a new branch copies everything from the master branch by default.
* Let's create a new branch called "bettercurrents": `git checkout -b bettercurrents`
* Copy this to your GitHub remote repo: `git push origin bettercurrents`
* To list all your branches, simply type `git branch`
Let's say you've finished adding your new features to your file "currents.m" and are satisfied it works as intended. 
You have already committed the changes to Git/GitHub. You can now "merge" this improved file back onto your master branch.
* Swap back to your master branch: `git checkout master`
* Merge your development branch into master: `git merge bettercurrents`
* If merge successful, you can safely delete the old branch: `git checkout -d bettercurrents`
* Push changes to GitHub: `git push origin master`


## Going back to previous versions of code
As mentioned right at the beginning, the core use of Git is to version control your code!
Say you had committed a change that didn't quite work.
Using Git, you can theoretically drop the change and fall back to a previously committed version that did work. 

I have never had to do this, so I'll refer you to this handy guide instead. 
https://stackoverflow.com/questions/4114095/how-to-revert-a-git-repository-to-a-previous-commit
and
https://code.likeagirl.io/how-to-undo-the-last-commit-393e7db2840b
 
