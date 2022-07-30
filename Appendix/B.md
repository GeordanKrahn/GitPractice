# Git Workflow

## **Trees**
- In many VCS's there are two main trees
- These are the Repository and the Working directories.
- we will *checkout* the current state from the repository
- we will *commit* staged changes from working directory
- in git there will be another directory called the staging index
    - Working -> `git add filename.ext` -> Staging Index -> `git commit filename.ext` -> Repository
    - This can work in reverse, but is typically not done
- After stages files are commited to the repository, the current state can then be *checked out*
## **Hash Values**
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
## **The HEAD**
- the ***HEAD*** is a pointer to the tip of the current branch of the repository
- This is what was most previously checked out
- will point to the parent of the next commit
- when a new commit is made the HEAD pointer will point to the next parent
- The HEAD can move between different branches in the repository