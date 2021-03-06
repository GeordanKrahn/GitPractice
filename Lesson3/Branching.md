[<< Lesson2](../Lesson2/CoreUsage.md) | **Lesson3** | [Lesson4 >>](../Lesson4/Remotes.md)

# Using Branches
*This is perhaps the most powerful aspect of version control. It is essential to be able to work in a team while not ruining eachothers work. Branches allow us to work on separate tasks without destroying the main branch. If the work is of good quality and little to no conflicts, then they will be merged. Branches with many conflicts or with poor quality code can be easily deleted without touching the main branch.*

**For this tutorial i will be describing what branches are and how to use them.**

**DISCLAIMER**
- *This tutorial uses examples for **Windows 10**. These instructions may differ for **Linux** and **Mac OSX**.*

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
3. [Merging](#merging)
    - A. [Merge](#merge)
    - B. [Conflicts](#conflicts)
    - C. [Resolving Conflicts](#resolving-conflicts)
    - D. [Avoiding Conflicts](#avoiding-conflicts)
4. [Stash Changes](#stash-changes)
    - A. [Saving](#saving)
    - B. [Viewing](#viewing)
    - C. [Receiving](#receiving)
    - D. [Deleting](#deleting)
5. [See Also](#see-also)

## Introduction

### Overview
When we make changes to our project, especially in a team, it becomes necessary to work on a set of changes in isolation, before adding those changes to the main branch.

- In Git, we start off with a **Main** branch.
- We can create branches off of the **Main**.
- We can create branches off of other branches too.
* [Return To Top](#contents)
### View Branches
- To view the branches in your repo, use `git branch`

    ![Branch](Images/Branch.PNG)
    - Here, **main** is the only branch
    - The current branch will be highlighted in green
* [Return To Top](#contents)
## Using Branches

### The Current Branch
- In the image above, there is only one branch
- Remember our HEAD, When we make a commit to another branch the HEAD will point to the other branch instead of main. This would be the current branch. 
- We can switch branches. HEAD will point to the most recent commit in the current branch.
* [Return To Top](#contents)
### Create New Branch
- use `git branch <branch name>` to create a new branch.

    ![Branch](Images/Branch2.PNG)
    - The branch name Cannot contain spaces.
    - The branch name Can contain letters, numbers and underscores.

- After creating the new branch, it will be listed in the branches when we use the `git branch` command

    ![Branch](Images/Branch3.PNG)
    - The branch *NewBranch* is listed
    - Notice that *main* is still the current branch
* [Return To Top](#contents)
### Switching Branches
- use the `git checkout <branch name>` command to switch to another branch.

    ![Branch](Images/Checkout.PNG)
    - notice which branch we are on, see the blue text

- We can now confirm we are on the new branch

    ![Branch](Images/Branch4.PNG)
    - The current branch is highlighted in green

- The following commands allow us to see the contents of the HEAD file in the .git directory. This is useful if you want to know what the HEAD points to.

    - On Linux or BASH

    ![Branch](Images/CAT.PNG)

    - On Windows

    ![Branch](Images/TYPE.PNG)

- ***Remember**, the HEAD always points to the most recent commit in a branch*

- Now that we are on the new branch, lets make some changes. I will create a folder with a single file, and edit a line in the README.md

    ![Branch](Images/File.PNG)

- using `git status` we can see the staging directory only retains changes on the current branch

    ![Branch](Images/Status.PNG)

- Once committed, if we switch back to the main branch using `git chechout main`. Note the structure of the directory after we switch. This is because main has been untouched by the changes to the other branch.

    ![Branch](Images/File2.PNG)

- We can create a branch and switch to it by using the `-b` flag for the `git checkout` command.

    ![Branch](Images/Checkout2.PNG)

- We do not need to be on main to create a new branch. A branch can be made anytime from the current branch. So if the current branch is called TestBranch and we create a new branch called NewTestBranch, it will be a branch of TestBranch.

- Suppose we make changes to the working directory on this new new branch. If we switch to main, those changes may be lost...

    ![Branch](Images/Checkout3.PNG)
    - luckily git aborts this task. Go back to the other branch and add or discard those changes. Then you can safely return to the main branch.

**Rules When Switching Branches With Un-Commited Changes**
```
    1.  Switching Branches is not possible if changes to the current
        branch conflict with the destination branch.
    
    2.  Switching is permissible if changes in the working directory 
        will not conflict with the destination branch.

    3.  Switching is permissible for untracked files.
```

   - *If there are conflicts, there are a few options. You may `commit` the changes, `discard` the changes, or `stash` the changes.*

* [Return To Top](#contents)
### Comparing Branches
- To compare a branch, just use `git diff <Branch name>..<Branch name>`

    ![Branch](Images/Diff.PNG)
* [Return To Top](#contents)
### Renaming Branches
- Use the `-m` flag of the `git branch` command to rename a branch
- `git branch -m <old branch> <new branch>`

    ![Branch](Images/Branch5.PNG)
    - Notice the new name in the blue text.
* [Return To Top](#contents)
### Deleting Branches
- Maybe your changes wont be useful, or have too many conflicts to merge. Whatever the case, you this branch is no longer useful.

    ![Branch](Images/Branch6.PNG)

- Delete a branch by using `-d` flag for the `git branch` command.
- `git branch -d <Branch name>`

    ![Branch](Images/Branch7.PNG)
    * ***NOTE:** YOU CANNOT DELETE THE **CURRENT BRANCH***
* [Return To Top](#contents)
### Resetting Branches
- Resetting will change the state of the files in the staging index and working directory for the desired commit.
- This will move the HEAD to point to the desired commit.

**There are 3 types of reset:**
```
    Soft
    - Moves the HEAD to the desired commit
    - Does not affect the staging or working directories
    Mixed
    - If not option is specified, this is the default.
    - Moves the HEAD to the desired commit
    - Changes the staging directory 
    - not the working directory.
    Hard
    - Moves the HEAD to the desired commit
    - Changes both the staging and working directories
```
- `git reset --soft` - performs a soft reset
    - rolls back to an old state but working and staging directories keep changes.
    - This can be a useful way amend a series of previous commits
    - after the reset the previous commits will be gone.
- `git reset` and `git reset --mixed` - performs a mixed reset
    - This leaves the working directory unchanged.
    - Can be used to reorganize commits
- `git reset --hard` - performs a hard reset
    - Rolls back and deletes all changes.
    - permanently destroys commits.
- try to avoid resetting shared commits.
- Mixed and Hard can be destructive, so be careful.
- `git reset [--mixed|--soft|--hard] <tree-ish>`

    ![Branch](Images/Reset.PNG)
* [Return To Top](#contents)
## Merging
- Merging allows us to add the changes from a branch to a recieving branch.
- There are 2 ways that a merge can occer
    - The both branches have there own changes before merge
    - only the separate branch has changes before merge
- The diagram below illustrates this concept
```
Both branches have changes:

    main1 -> main2 -> main3 -> main4 -> main5 -> main6
              \                                  /
                - branch1 -> branch2 -> branch3 -
```
```
Only one branch has changes:

    main1 -> main2 ---------------------------> main3
              \                                  /
                - branch1 -> branch2 -> branch3 -

```
* [Return To Top](#contents)
### Merge
- Lets assume changes were made

    ![Branch](Images/File3.PNG)

    ![Branch](Images/Log.PNG)

- First, change to the branch which will recieve changes

    ![Branch](Images/Checkout4.PNG)

- Note the log

    ![Branch](Images/Log2.PNG)
    - Use `git diff <Branch>..<Branch>` to compare the changes.

- Use `git merge <Branch>` to merge the changes on the other branch, to the current branch. If there are any conflicts, you will need to resolve them..

    ![Branch](Images/Merge.PNG)

- You may want a visual representation of your repository
- use `git log --graph`. The `--graph` flag will display a text representation of the structure of the repo.
- Can combine with other formatting flags

    ![Branch](Images/Log3.PNG)
    ```
    --all       - displays all refs in refs/ as commits. 
    --decorate  - prints out the ref names of the commits. 
    --oneline   - condenses the data to a single line.
    ```
* [Return To Top](#contents)
### Conflicts
- Conflicts occur when changes to the same lines in files appear on both branches.
- You will need to decide which branches changes you want to keep.
- The following is a representation of this.

    ![Branch](Images/Log4.PNG)

- The following is what happens when a merge is attempted.

    ![Branch](Images/Merge2.PNG)
* [Return To Top](#contents)
### Resolving Conflicts
- You can abort the merge, manually handle the changes, or let a tool handle the merge conflict. I will demonstrate how to manually handle the changes.
- Your text editor should pop open after this so you can fix the conflicts. If not, you should inspect the files which are causing the conflicts and attempt to fix them.

    ![Branch](Images/File4.PNG)
    - Visual Studio Code is one of many powerful editors available. Save the changes to the file and git should handle the rest of the merge.

- After saving, make sure to add and commit those changes, or the merge wont work.

    ![Branch](Images/Merge3.PNG)

- Now lets look at the branches

    ![Branch](Images/Log5.PNG)

- To abort the merge while in the MERGING state, use the `--abort` flag for the `git merge` command.
* [Return To Top](#contents)
### Avoiding Conflicts
**To prevent conflicts from occuring:**
- try keeping changes atomic (single line changes)
- try to keeps commits atomic as well.(one or few changes)
- Avoid creating whitespace in files
- Merge changes frequently.

## Stash Changes
- The stash is another directory in your git repository
- When you need to switch branches, but you have changes in your working directory, you can stash the changes for later.
- By default, `git stash` does not save untracked files, as these wont cause conflicts
    - To stash untracked files, use the `-u` flag

    ![Branch](Images/File5.PNG)

- When attempting to switch branches, the following error appears

    ![Branch](Images/Checkout5.PNG)
    - One obvious way to fix this is by commiting your changes, but we can use the stash to store these changes if needed.

- When you stash changes, they will be available from all other branches.
* [Return To Top](#contents)
### Saving
- Use `git stash save "title"` to stash your changes

    ![Branch](Images/Stash.PNG)
    - Note the status after stashing

- After stashing, the working directory is now empty.
* [Return To Top](#contents)
### Viewing
- Use the `git stash list` command to view a set of changes in the stash without loading them.

    ![Branch](Images/Stash2.PNG)
    - the stash is a pointer to a set of changes.
    - note the syntax `stash@{0}`.
    - the `{}` contain the index for the stash.

- Use `git stash show -p Stash@{index}` command to view the changes.
    - `-p` allows us to see what the changes are.

    ![Branch](Images/Stash3.PNG)
* [Return To Top](#contents)
### Receiving
- use `git stash pop` command to add the stash to the working directory. Be careful of conflicts. Resolve them first.
- Can also use `git stash apply`, which does not remove the changes from the stash.

    ![Branch](Images/Stash4.PNG)
    - Notice how the stash list is empty, `pop` removes the stashed changes.
    - use `apply` to load the changes without removing the stash.
* [Return To Top](#contents)
### Deleting
- `pop` will delete the entry after it is loaded.
- If you use `apply` to load changes and end up committing them, make sure you delete the stash for those changes.
- use `git stash drop stash@{index}` to remove the stashed changes.

    ![Branch](Images/Stash5.PNG)

- use `git stash clear` to remove all sets of stashed changes
* [Return To Top](#contents)
## See Also
- **[Lesson 4: Working With Remotes](../Lesson4/Remotes.md)**
- **[Appendix](../Appendix/Appendix.md)**
- **[Main Menu](../README.md)**
* [Return To Top](#contents)