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
2. [Understanding the Trees](#understanding-the-trees)
    - A.  [Working Directory](#a-working-directory)
    - B.  [Staging Directory](#b-staging-directory)
    - C.  [Repository](#c-repository)
    
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

### B. Git Diff

### C. Git Show

### D. Git Log

## Understanding the Trees

### A. Working Directory

### B. Staging Directory

### C. Repository