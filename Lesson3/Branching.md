# Using Branches

## Contents
1. [Introduction](#introduction)
    - A. [Overview](#overview)
    - B. [View Branches](#view-branches)
2. [Using Branches](#using-branches-1)
    - A. [The Current Branch](#the-current-branch)
    - B. [Create New Branch](#create-new-branch)
    - C. [Switching Branches](#switching-branches)
    - D. [Comparing Branches](#comparing-branches)
    - E. [Renaming Branches](#renaming-branches)
    - F. [Deleting Branches](#deleting-branches)
    - G. [Resetting Branches](#resetting-branches)
    - H. [Merging](#merging)
3. [See Also](#see-also)

## Introduction

### Overview
When we make changes to our project, especially in a team, it becomes necessary to work on a set of changes in isolation, before adding those changes to the main branch.

- In Git, we start off with a **Main** branch.
- We can create branches off of the **Main**.

### View Branches
- To view the branches in your repo, use `git branch`

    ![Branch](Images/Branch.PNG)
    - Here, **main** is the only branch
    - The current branch will be highlighted in green

## Using Branches

### The Current Branch
- In the image above, there is only one branch
- Remember our HEAD, When we make a commit to another branch the HEAD will point to the other branch instead of main. This would be the current branch. 
- We can switch branches. HEAD will point to the most recent commit in the current branch.

### Create New Branch
- use `git branch <branch name>` to create a new branch.

    ![Branch](Images/Branch2.PNG)
    - The branch name Cannot contain spaces.
    - The branch name Can contain letters, numbers and underscores.

- After creating the new branch, it will be listed in the branches when we use the `git branch` command

    ![Branch](Images/Branch3.PNG)
    - The branch *NewBranch* is listed
    - Notice that *main* is still the current branch

### Switching Branches
- use the `git checkout <branch name>` command to switch to another branch.

    ![Branch](Images/Checkout.PNG)
    - notice which branch we are on, see the blue text

- We can now confirm we are on the new branch

    ![Branch](Images/Branch4.PNG)
    - The current branch is highlighted in green

### Comparing Branches

### Renaming Branches

### Deleting Branches

### Resetting Branches

### Merging

## See Also
- **[Lesson 4: Working With Remotes](../Lesson4/Remotes.md)**
- **[Appendix](../Appendix/Appendix.md)**
- **[Main Menu](../README.md)**