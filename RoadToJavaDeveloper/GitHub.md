# Road To Becoming A Java Developer
## Unit 1: **GitHub**
GitHub is a version control system which allows multiple developers to contribute and work on a single project at same time as one another. Repositories are stored on GitHub, as well as the user's local machine. This allows authors to create changes to the files on their local machine, verify that it doesn't break anything, all before pushing this new file or version to the rest of the authors / users. 
### **Congifuration:**
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
* Installs a cleaner, more user friendly (and fraknly modern) terminal appearance.
    * On macOS, use Zsh with Git plugin.
### **Cheat Sheet**
Here is a useful Git Cheat Sheet created by the YouTuber ["Programming with Mosh"](https://www.youtube.com/channel/UCWv7vMbMWH4-V0ZXdmDpPBA). He's an excellent teacher and his videos are always very high quality. Great resource.

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
>git add.
* Adds all changes that have been made in your local repository to the actual repository.
> git remote add origin https://github.com/userName/repoName.git
* This command allows you to push an existing local repository by adding a remote repository to your local one. This allows you to do all other remote operations (push, pull, feth, etc.). Note: If you have created your local repository using the command line, then do not worry about this command.
