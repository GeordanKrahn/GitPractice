# Git Commands

## **These are some useful commands**

|Command|Description|
|---|---|
|`git help <command>`|displays the usage information for the specified command|
|`git init`|initializes a git repository|
|`git add <filepath>`|adds files or changes to the git repo for later commit.|
|`git add .`|adds the current directory to be commited later. this is the common command|
|---|---|
|`git commit -m "<commit message>"`||
||Staged changes added to the git repository. 
||Must have a commit message. 
||Try to keep the message single line and under 50 characters.
||Start with the single line, then can move on to multi line messages if necessary. 
||Try to keep 72 characters or less for multiline. 
||Keep the messages in present tense for what the changes are actually doing. 
||Bullet points are usually asterisks or hyphens [*, -]. 
||Can add tracking numbers such as `#9` if there is a specific issue you would like to be referenced in the message. 
||Can use some other shorthand for your organisation such as `bugfix: <message>`.
||Make them clear and descriptive and to the point.|
|---|---|
|`git commit`||
||not supplying `-m` flag will allow for a multiline commit message.| 
||changes will be commited when the message file is saved. Empty messages will abort commit.
|---|---|
|`git commit -a`||
||commonly used with `-m` flag, staged tracked files in working directory AND commits them to repository.| 
||Untracked files and changes will be ignored. 
||Dropping `-m` flag allows multiline commit message.|
|---|---|
|`git commit --amend`|pulls the previous commit back into staging, adds the current staging files, and updates the commit message.|
|`git push`|uploads all local branch commits to the corresponding remote branch git repository|
|`git pull`|pulls the current state, makes our working copy up to date|
|`git status`|displays information about the current state of our repository|
|---|---|
|`git log`||
||Displays information about the commit history|
||**commit ID** is a ***SHA-1* Hash** identifies the commit
||**Author: Geordan Krahn <someEmail@email.com>** - The user and email associated with the commit
||**Date: Sun May 15 15:26:27 2022 -0600** - Date and time of the commit
||**add the git log command to the readme.md** - Commit message|
|---|---|
|`git log -n #`|limits how many results to return to the terminal|
|`git log -n 3`|will only display the 3 most recent commits|
|`git log --since=yyyy-mm-dd`|displays all commits going back to the date specified|
|`git log --until=yyyy-mm-dd`|displays all commits going to the date specified|
|`git log --author=<partialString>`|displays all commits from a specified author|
|---|---|
|`git log --grep=<regex>`|can use regular expressions specified as a string|
||To exit the log before or when you reach the `(END)` statement you can press `q`.
||To display a full page of results at once, press `z`.|
|---|---|
|`git show <SHA-1>`|displays only the commit. Can use partial search for SHA-1 for that commit|
|---|---|
|`git diff`||
||This will display the changes to unstaged files
||NOTE: This will only work on unstaged files.
||Highly recommended to see more info regarding diff command by using the help command
|---|---|
|`git diff --staged`||
||display changes to stages files
||To exit the diff tool before or when you reach the `(END)` statement you can press `q`.
||To display a full page of changes at once, press `z`.|
|---|---|
|`git diff <old commit SHA-1>..<new commit SHA-1>`||
||displays changes between 2 specified commits
||can use HEAD as argument, will use the SHA-1 for where the HEAD points to.|
|---|---|
|`git rm <filename>`||
||removes a file from the project
||NOTE: git will automatically stage the changes when this command is used to delete files.
|---|---|
|`git rm -r <folderName>`|remove an entire folder and its contents|
|`git rm -r --cached <folderName>`|remove folder from Git, but NOT your filesystem|
|`git mv <filename> <newFilename>`|This command can both move a file somewhere else, AND rename a file aswell|
|`git mv someFile.txt someOtherFile.txt`|Rename a file or folder|
|---|---|
|`git mv someFile.txt someFolder/someFile.txt`||
||Move a file or folder
||NOTE: If the folder did not already exist, you will need to create it.|
|---|---|
|`git checkout <SHA-1> -- <filename>`|This will revert a file back to an older version using the SHA-1 from the commit for the version you may need|
|`git restore <filename>`|discards changes to the working directory|
|`git restore --staged <filename>`|discards staged changes, places them back into working directory|
|`git restore --staged --working <filename>`|discards changed to both staged directory and working directory|
|`git revert <SHA-1>`|creates a new commit which takes the old configuration from the SHA-1 provided. This does NOT undo changes, just supplies the old configuration as new changes in the history.|
|`git ls-tree <SHA-1>`|Lists the tree contents|
|---|---|
|`git clean -<flag> <filename>`||
||remove untracked from the working directory, must use flags
||**Be careful**, this is a ***destructive process*** and you may not want to lose the new files you are working on. 
||You may want to consider adding them, then removing the files from the project using `git rm -r <filename>` instead and then add it to your **.gitignore**. This way you will have a history of these changes.|
|---|---|
|`git clean -i`|interactive mode - shows what *would* be deleted, and allows interactive cleaning|
|`git clean -n`|does a *dry run* and shows you what changes *would* be made|
|`git clean -f`|deletes the untracked files|
|`git clean -d`|recurses into untracked directories. does nothing if any path is specified|