# Git Information

- **This file will contain git commands and other important information on Git usage and workflows**
- **You will need Git installed on your system**
- **You can find Git [here](https://git-scm.com/)**


## Contents
1.  [Lessons](#lessons)
2.  [Git Commands](#git-commands)
3.  [Workflow](#git-workflow)
4.  [GitHub Commands](#github-commands)

## Lessons
- **[Lesson 1: Setup Tutorial](Lesson1/Setup.md)**
- **[Lesson 2: Core Usage](Lesson2/CoreUsage.md)**
## Git Commands
- `git help <command>` - displays the usage information for the specified command
- `git init` - initializes a git repository
- `git add <filepath>` - adds files or changes to the git repo for later commit.
    - `git add .` - adds the current directory to be commited later. this is the common command
- `git commit -m "<commit message>"` - staged changes added to the git repository. Must have a commit message
    - try to keep the message single line and under 50 characters
    - Start with the single line, then can move on to multi line messages if necessary
        - try to keep 72 characters or less for multiline
        - keep the messages in present tense for what the changes are actually doing
        - Bullet points are usually asterisks or hyphens [*, -]
        - Can add tracking numbers such as `#9` if there is a specific issue you would like to be referenced in the message
        - Can use some other shorthand for your organisation such as `bugfix: <message>`
        - make them clear and descriptive and to the point
    - `git commit` - not supplying `-m` flag will allow for a multiline commit message. changes will be commited when the message file is saved. Empty messages will abort commit.
    - `git commit -a` - commonly used with `-m` flag, staged tracked files in working directory AND commits them to repository. Untracked files and changes will be ignored. Dropping `-m` flag allows multiline commit message.
    - `git commit --amend` - pulls the previous commit back into staging, adds the current staging files, and updates the commit message.
- `git push` - uploads all local branch commits to the corresponding remote branch git repository.
- `git pull` - pulls the current state, makes our working copy up to date
- `git status` - displays information about the current state of our repository
- `git log` - Displays information about the commit history
    -   **commit 708c6dac011fe676a480742a48f68278a0d22e1d (HEAD -> main)**  - commit ID is a ***SHA-1* Hash** identifies the commit
    -   **Author: Geordan Krahn <someEmail@email.com>** - The user and email associated with the commit
    -   **Date: Sun May 15 15:26:27 2022 -0600** - Date and time of the commit
    -   **add the git log command to the readme.md** - Commit message
    - `git log -n #` - limits how many results to return to the terminal
    - `git log -n 3` - will only display the 3 most recent commits
    - `git log --since=yyyy-mm-dd` - displays all commits going back to the date specified
    - `git log --until=yyyy-mm-dd` - displays all commits going to the date specified
    - `git log --author=<partialString>` - displays all commits from a specified author
    - `git log --grep=<regex>` - can use regular expressions specified as a string
    - To exit the log before or when you reach the `(END)` statement you can press `q`.
    - To display a full page of results at once, press `z`.
- `git show <SHA-1>` - displays only the commit. Can use partial search for SHA-1 for that commit
- `git diff` - This will display the changes to unstaged files
    - NOTE: This will only work on unstaged files.
    - Highly recommended to see more info regarding diff command by using the help command
    - to view changes to staged files, use the `--staged` OR `--cached` flags
        - `git diff --staged`
    - To exit the diff tool before or when you reach the `(END)` statement you can press `q`.
    - To display a full page of changes at once, press `z`.
    - `git diff <old commit SHA-1>..<new commit SHA-1>` - displays changes between 2 specified commits
    - can use HEAD as argument, will use the SHA-1 for where the HEAD points to.
- `git rm <filename>` - removes a file from the project
    - NOTE: git will automatically stage the changes when this command is used to delete files.
    - to remove an entire folder and its contents:
        - `git rm -r <folderName>`
    - To remove folder from Git, but NOT your filesystem:
        - `git rm -r --cached <folderName>`
- `git mv <filename> <newFilename>` - This command can both move a file somewhere else, AND rename a file aswell.
    - to rename:
        `git mv someFile.txt someOtherFile.txt`
    - to move else where:
        `git mv someFile.txt someFolder/someFile.txt`
    - NOTE: If the folder did not already exist, you will need to create it.
- `git checkout <SHA-1> -- <filename>` - This will revert a file back to an older version using the SHA-1 from the commit for the version you may need.
- `git restore <filename>` - discards changes to the working directory
    - `git restore --staged <filename>` - discards staged changes, places them back into working directory
    - `git restore --staged --working <filename>` - discards changed to both staged directory and working directory
- `git revert <SHA-1>` - creates a new commit which takes the old configuration from the SHA-1 provided. This does NOT undo changes, just supplies the old configuration as new changes in the history.
- `git ls-tree <SHA-1>` - Lists the tree contents

## Git Workflow
-  **Trees:**
    - In many VCS's there are two main trees
    - These are the Repository and the Working directories.
    - we will *checkout* the current state from the repository
    - we will *commit* staged changes from working directory
    - in git there will be another directory called the staging index
        - Working -> `git add filename.ext` -> Staging Index -> `git commit filename.ext` -> Repository
        - This can work in reverse, but is typically not done
    - After stages files are commited to the repository, the current state can then be *checked out*
- **Hash Values:**
    - Git refers to the snapshot of changes as a *hash value*
    - Git will generate a *checksum* for each change set
    - Checksum algoriths convert the data into a number
    - This is a lossless algorithm where the same data will always yield the same checksum value
    - Guaruntees Data Integrity
    - Git uses the ***SHA-1*** hash algorithn to create checksums
    - SHA-1 hash values are 40 character hexadecimal strings
        - ex: `bad17599f7a241e4873aba2401343452b6f41084`
    - Git also uses the metadata associated within each snapshot
        - such as the parent, author, message, etc...
    - if we have a snapshot A and the commit changes, then the snapshot B will include the metadata from A for its Hash
- **The HEAD:**
    - the ***HEAD*** is a pointer to the tip of the current branch of the repository
    - This is what was most previously checked out
    - will point to the parent of the next commit
    - when a new commit is made the HEAD pointer will point to the next parent
    - The HEAD can move between different branches in the repository

## GitHub Commands
- **Github CLI is *optional*. I will include some useful commands here. You must have it installed on your system just like Git**
- **You can find the CLI [here](https://cli.github.com/)**