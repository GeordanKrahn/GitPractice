# Git Commands

**This file will contain git commands**

- `git help <command>` - displays the usage information for the specified command
- `git init` - initializes a git repository
- `git add <filepath>` - adds files or changes to the git repo for later commit.
    - `git add .` - adds the current directory to be commited later. this is the common command
- `git commit -m "<commit message>"` - stages our changes to the git repository. Must have a commit message
    - try to keep the message single line and under 50 characters
    - Start with the single line, then can move on to multi line messages if necessary
        - try to keep 72 characters or less for multiline
        - keep the messages in present tense for what the changes are actually doing
        - Bullet points are usually asterisks or hyphens [*, -]
        - Can add tracking numbers such as `#9` if there is a specific issue you would like to be referenced in the message
        - Can use some other shorthand for your organisation such as `bugfix: <message>`
        - make them clear and descriptive and to the point
- `git push` - uploads all local branch commits to the corresponding remote branch git repository.
- `git status` - displays information about the current state of our repository
- `git log` - Displays information about the commit history
    -   `commit 708c6dac011fe676a480742a48f68278a0d22e1d (HEAD -> main)`  - commit ID uniquely identifies the commit
    -   `Author: Geordan Krahn <someEmail@email.com>` - The user and email associated with the commit
    -   `Date: Sun May 15 15:26:27 2022 -0600` - Date and time of the commit
    -   `add the git log command to the readme.md` - Commit message
- `git log -n #` - limits how many results to return to the terminal
    - `git log -n 3` - will only display the 3 most recent commits
    - `git log --since=yyyy-mm-dd` - displays all commits going back to the date specified
    - `git log --until=yyyy-mm-dd` - displays all commits going to the date specified
    - `git log --author=<partialString>` - displays all commits from a specified author
    - `git log --grep=<regex>` - can use regular expressions specified as a string


        