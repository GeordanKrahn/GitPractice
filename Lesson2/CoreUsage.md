[<< Lesson1](../Lesson1/Setup.md) | **Lesson2** | [Lesson3 >>](../Lesson3/Branching.md)

# Core Usage Tutorial
**For this tutorial, I will be walking you through the most common functionality of git. This guide is an ongoing process and will be continously updated**


**DISCLAIMER**
- *This tutorial uses examples for **Windows 10**. These instructions may differ for **Linux** and **Mac OSX**.*

## Contents
1. [Information Commands](#information-commands)
    - A.  [Git status](#a-git-status)
    - B.  [Git diff](#b-git-diff)
    - C.  [Git show](#c-git-show)
    - D.  [Git log](#d-git-log)
2. [Core Use](#understanding-the-trees)
    - A.  [Working Directory](#a-working-directory)
    - B.  [Staging Directory](#b-staging-directory)
    - C.  [Repository](#c-repository)
3. [See Also](#see-also)
    
## Information Commands
- The following commands can tell you what the current state (or previous state) your repository is in.

### A. Git Status
- In your current git repo, typing `git status` will display what the current state is.

    ![Git Status](Images/Status1.PNG)

- This is only an empty directory, so nothing is being tracked right now.
- By adding files and then using `git status`, we now have ***untracked files***

    ![Git Status](Images/Status2.PNG)

- This shows we have a README.md in our **Working Directory**, but it is not being tracked
- Since README.md is a good starting file, we should use `git add README.md` to begin tracking this file

    ![Git Status](Images/Status3.PNG)

- README.md is now in the **Staging Index**, a directory which holds onto our changes before we commit them
- Now we will commit the file
    - NOTE: you ***must*** supply a commit message using the `-m` flag. 
        - Omitting this flag allows for a multiline comment 
        - Your text editor will open up a special file where you can enter in a multiline comment. 
        - When finished, save and exit and the commit will finish. 
        - Supplying an empty commit message will abort the commit.

    ![Git Status](Images/Status4.PNG)

- `git status` now tells us that there is nothing to commit, and the working tree is clean.
    - NOTE: The working tree is where we actively make changes to our repository, but nothing is final here until will `git add <file>` the changes

- Lets add some content to the README.md...

    ![Content](Images/Content1.PNG)

- use `git status`

    ![Git Status](Images/Status5.PNG)

- Now status tells us that a **Tracked file** has been modified in our *Working Directory*
- If we are satisfied, we can now add it to the *staging directory*

    ![Git Status](Images/Status6.PNG)

- and from here we can now commit our changes

    ![Git Status](Images/Status7.PNG)
* [Return To Top](#contents)
### B. Git Diff
- The Following Command will show you a comparrison between your working tree and a commit
- `git diff` - This will display the changes to unstaged files

    ![Git Status](Images/Diff1.PNG)
    - To exit the diff tool, press `q`.
    - To display a full page, press `z`.
    - To print next line press `Enter`.
- after adding using `git add <filename>`, the files will be *'staged'*

    ![Git Status](Images/Diff2.PNG)

- the diff command no longer does anything

- `git diff --staged` - to view changes to staged files

    ![Git Status](Images/Diff3.PNG)

- `git diff <old commit SHA-1>..<new commit SHA-1>` - displays changes between 2 specified commits

    ![Git Status](Images/Diff4.PNG)
    - can use HEAD as argument, will use its SHA-1.
    - using `~n` where n is any number of parent levels to go back will replace with the argument with the necessary SHA-1 for that commit

* [Return To Top](#contents)
### C. Git Show
- When we only want to view a single commits changes in isolation, we can use `git show`

- `git show <Sha-1>` shows all changes for the commit associated with the Sha-1.

    ![Git Status](Images/Show.PNG)
    - If the Sha-1 is unspecified, will use the current HEAD Sha-1.
    - Can use HEAD to specify SHA-1
        - ~n to go back n number of commits
        - ^ to go back a single commit
    - Like the Diff Tool, To exit, press `q`.
    - To display a full page, press `z`.
    - To print next line press `Enter`.
* [Return To Top](#contents)
### D. Git Log
- `git log` - Displays information about the commit history

    ![Git Status](Images/Log.PNG)

- `commit 708c6dac011fe676a480742a48f68278a0d22e1d (HEAD -> main)`
    - `Commit ID` is a SHA-1 Hash which identifies the commit

- Some important information associated with each commit:
    - `Author` - The user and email associated with the commit
    - `Date` - Date and time of the commit
    - `Commit message` (All commits must have one)

- We can specify which commits we want to see in the commit history, our log.

- Useful Flags:
    - `-n #` - limits how many results to return to the terminal
    - `-n 3` - will only display the 3 most recent commits
    - `--since=yyyy-mm-dd` - displays all commits going back to the date specified
    - `--until=yyyy-mm-dd` - displays all commits going to the date specified
    - `--author=<partialString>` - displays all commits from a specified author
    - `--grep=<regex>` - can use regular expressions specified as a string
- To exit the log before or when you reach the (END) statement you can press `q`.
- To display a full page of results at once, press `z`.
- To print the next line, press `Enter`.
* [Return To Top](#contents)
## Understanding the Trees
- To make the most out of using git, you should understand the trees
### A. Working Directory
- The working directory is where all of your current changes are made. 
- These changes may include tracked files with changes, or entirely new files which will need to be tracked.
- To begin tracking files, or changes, you will need to add the changes to the staging directory
- It is good practice to use `git status` to view your *untracked* changes.
- You may also use `git diff`
- DO review your changes before staging them.
- `git add <filename>`

    ![Git Status](Images/Add.PNG)
    - `git add .` this adds all changes in the current folder and all subfolders.
* [Return To Top](#contents)
### B. Staging Directory
- The staging directory is where all changes will remain until they are commited, or unstaged.
- It is good practice to use `git status` to view your *tracked* changes.
- You may also use `git diff --staged`
- DO review your changes before committing them.
- `git commit -m`

    ![Git Status](Images/commit.PNG)
* [Return To Top](#contents)
### C. Repository
- This directory is where the tracked changes are saved.
- Once a change has made it to this point, we will have a rigid history of that change until we delete our repository.
- We can remove changes, however this is highly discouraged, as we should want to keep track of every change to our repo.
- To properly remove a change but still have a history, use the `git rm --cached` command
- If you have a `remote` repo set up, you can push your local changes to your remote from this point.
- If you are using BASH, you will need your `username` and `personal access token` to push.
- If you are using a tool which allows Github integration (or another remote VCS) you should be signed in. (ex. Visual Studio Code)

    ![Git Status](Images/push.PNG)
    - Here we have no remote set up

    ![Git Status](Images/push2.PNG)
    - Here we have a remote set up
* [Return To Top](#contents)
## See Also
- **[Lesson 3: Using Branches](../Lesson3/Branching.md)**
- **[Appendix](../Appendix/Appendix.md)**
- **[Main Menu](../README.md)**
* [Return To Top](#contents)