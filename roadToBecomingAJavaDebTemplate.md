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
* Opens your core editor to allow you to edit all of the global settings.