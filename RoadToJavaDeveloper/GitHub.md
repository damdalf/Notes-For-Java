# Road To Becoming A Java Developer
## Unit 1: **GitHub**
GitHub is a version control system which allows multiple developers to contribute and work on a single project at same time as one another. Repositories are stored on GitHub, as well as the user's local machine. This allows authors to create changes to the files on their local machine, verify that it doesn't break anything, all before pushing this new file or version to the rest of the authors / users. 

***
### **CONFIGURATION:**
Settings:

* Name
* Email
* Default editor
* And how Git should handle line endings

Three different levels of Settings:

* System - Apply to all users of the current computer.
* Global - Apply to all repositories of the current user.
* Local - Apply to the current repository.

> git config --global user.name "insertName"
* Sets your username.
>git config --globaal user.email insertEmail
* Sets your email address.
>git config --global core.editor "code --wait"
* Sets your core editor.
>git config --global -e
* Opens your core editor to allow you to edit all of the global settings. Note how GitBASH / your terminal waits for you to close the config file in your core editor. Simply save any changes and then close the file.
>git config --global core.autocrlf true
* Windows uses [\r][\n] line returns while macOS uses [\n]. The following command tells Git to only edit end-of-line characters when storing code in the respository.
    
    * Windows user: finish the command with true as is done in the above example.
    * macOS or Linux user: replace "true" with "input".
>git config --help
* Opens the Git Configuration Help Page inside your terminal. This is extremely useful. Press space to go to the next page, and q to close the page. 
>git config -h
* This gives us a short summary of this command and its options.
>posh-git
* Installs a cleaner, more user friendly (and fraknly more modern) terminal appearance. However, the installation process is rather long and far more complex than the single command above. Do so at your own desire.
    * On macOS, use Zsh with Git plugin.

***
### **CHEAT SHEET**
Here is a useful Git Cheat Sheet created by the YouTuber ["Programming with Mosh"](https://www.youtube.com/channel/UCWv7vMbMWH4-V0ZXdmDpPBA). He's an excellent teacher and his videos are always very high quality. Great resource.

***
### **SNAPSHOTS**
>mkdir "directoryName"
* Creates a new empty directory.
>git init "repositoryName"
* Creates a new Git repository in that directory, which doesn't have to be empty.
>ls
* Lists the important files under that directory.
> ls -a
* Lists ALL the files under that directory (including .git files).
>code
* Opens your chosen core editor.
>code .
* Opens the current directory in your chosen core editor.
>git status
* Returns the status of your current changes in the repository.
>rm -rf .git
* Removes the git sub-directory. You will no longer have a git repository at this directory.

### **USEFUL SHORTCUTS IF THINGS START HAVING ISSUES**
>git show-ref
* This command will show you your branch reference.
>git add .
* Adds all changes that have been made in your local repository to the actual repository.
>git add -u
* Updates all of your changes that have been made. Useful when files have been removed from the local repository. 
> git remote add origin https://github.com/userName/repoName.git
* This command allows you to push an existing local repository by adding a remote repository to your local one. Note: If you have created your local repository using the command line, then do not worry about this command.
>git remote add origin https://userName@github.com/userName/repoName.git
* Accomplishes the same results as the command above, but this is for when your repository is private. 
>git remote get-url origin
* This command returns the URL of your remote repository, also known as the 'origin'. 
>git remote rm origin
* This command removes the current remote origin.
.git push --set-upstream origin master
* This command adds an upstream branch to your 'master' branch. This allows you to do all other remote operations (push, pull, feth, etc.).
>git fetch origin
* Gathers any commits from the target branch of the remote repository that do not exist in your current branch and stores them in your local repository. Note, it does not **merge** them with your current branch.
>git pull origin master
* Updates your current HEAD branch with the latest changes from the remote server. This pull not only downloads new data, it also directly integrates it into your current working files. Thus, it is reccomended that you only 'pull' when you have no uncommitted local changes.
>git log
* Returns the log of all changes made. Press 'q' to exit this screen, or 'h' for help.

***
### **GIT WORKFLOW**

##### **GENERAL IDEA**
1. Change the repository locally in some way (add file, remove file, change folder organization, etc.).
2. Commit these changes when your project has reached a state that you wish to record. Creating a commit is like taking a "snapshot" of our project.

     * Git has a special area that doesn't exist in most other version control systems. It is called the "staging area" or "index", and it's basically what we're proposing for the next commit or snapshot.
     * So when you're done making changes, we add the files to the staging area, review our changes, and if everything checks out, then we make a commit.
     * The proposed snapshot will geet permanently stored in your repository. The staging area allows us to review our work before recording a snapshot. If some of the changes shouldn't be recorded as the next snapshot, we can unstage them and commit them as another snapshot. 
3. Push these changes to the remote repository target branch. 

It is best to ensure that your local repository is up-to-date with the remote repository by fetching origin, and then pulling.
***
>git add fileName.format
* Adds the new file to the staging area, or if a deletion of a file occurred, removes the file from the staging area.

*** 
### **STAGING FILES**

