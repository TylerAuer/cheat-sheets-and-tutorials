# GIT NOTES

## Random Bits

- Best practice to `$ git pull` before `$ git push`
- Can issue (most) git commands from anywhere in the directory
- Using git to rename (`$ git mv old_name.ext new_name.ext`) helps git recognize that the file is renamed. If you use the file system it will think a file was deleted and then a new file was created.
- If you are working on a feature branch but the master branch has advanced, you can `rebase` the master changes into your branch to incorporate the changes without merging

## Key Terms
- Repositories
- Workflow:
  1. Working Directory - Local folder that holds all of your files
  2. Staging Area (AKA Index) - Queued up files, ready for the next commit which push them to the local git repository 
  3. Git Local Repository - in a `/.git` folder holds all of the git files and histories
  4. Github External Repository
- **Branches** - `master` is the default branch
- `HEAD` - Refers to the most recent commit in the current branch
- **Fast-forward Merge** - Is a merge where the branch being merged was ahead **AND** no changes had been made of on the destination branch. In otherwords, branch off master, make 5 commits and then merge. Since the master did not have any changes after you split off your branch, then the branch's commits can just get put right onto the master branch. This "fast-forwards" the master branch.

## Commands Explained

**`$ git push origin master`**
- `git` - Using the program git
- `push` - Command to send changes to github
- `origin` - Something to do with the name of the github repo
- `master` - The branch you are pushing

**`$ git add`** - Add files to index (staging area)

- `$ git add .` - Recursively add all files to index
- `-A` Flag - Adds all files recursively but also updates any files that have been renamed or moved
- `-u` - Updates the index for the whole dir but doesn't add files

**`$ git commit -m "commit message"`** - Commits stages files

- `$ git commit -am "commit message"` - Stages any changed files and then commits in one step. Good for simple changes
- `$ git commit --amend` - Combines any staged changes with the most recent commit.
- `$ git commit --amend -m "Message"` - Updates the last commit's message

**`$ git ls-files`** - List all files currently being tracked in the repo

**`$ git reset Head [filename.ext]`** - Returns file to most recent commit, but maintains the changes made after the commit. Need to use `$ git checkout -- [filename.ext]` to revert to the state at the last commit.

**`$ git mv old_filename.ext new_filename.ext`** - Renames a file

**`$ git log`** - Shows a history of commits with newest commits at the top

- `-2` or `-10` - Shows the most recent *n* commits (can be other numbers)
- `-p` - "Patched" shows the differences

**`$ git diff`** - Shows diffs between modified and staged files by default

- `git diff HEAD` - Will compare working directory and latest commit (`HEAD`)
- `$ git difftool` - Opens program set as difftool to view the changes, takes the same parameters as `git diff`
- `$ git diff --staged HEAD` - Compares the staged area to the `HEAD` (the last commit)
- `$ git diff -- [path/to/diff.ext]` - Only shows the changes within one file
- `$ git diff HEAD HEAD^` - Compares most-recent and second-most recent commits in current branch
- `$ git diff master origin/master` - compares the HEAD of the two listed sources

**`$ git branch` and `$ git checkout`**

- `$ git branch -a` - lists all branches
- `$ git checkout [branch_name]` - switches branches
- `$ git checkout -b [branch_name]` - creates a new branch and switches to it
- `$ git branch -d [branch_name]` - deletes the branch (useful after merging)

**`$ git merge`**

- Must be a on the branch you want to merge into
- Use `$ git merge [branch_name] --no-ff` - to ensure that the branching is preserved even if the branch is then deleted

## Command Line Commands

**`$ ls`** - Lists all files in working directory

- `-a` - shows hidden files too
- `-l` - shows a long list of files
- `-R` - shows folders recursively
- `-h` - shows files sizes in human readable format 

**`$ unzip path/to/zip/file.zip`** - Unzips file to working directory

**`$ mv old_filename.ext new_filename`** -- Renames and/or moves a file

## Setting up Aliases

`$ git config --global alias.[name] "full command (excluding git) to be aliased to [name]"`

- Aliases live in `~/.gitconfig` file

## .gitignore

Lives inside root of each repo

- One file per line
- Each line can be:
  - A specific file: `file_name.ext`
  - A folder: `folder-name/`
  - An extension: `*.ext`