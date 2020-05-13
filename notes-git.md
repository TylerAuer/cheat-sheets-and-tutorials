# GIT NOTES

## Random Bits

- Best practice to `$ git pull` before `$ git push`

## Key Terms
- Repositories
- Workflow:
  1. Working Directory - Local folder that holds all of your files
  2. Staging Area (AKA Index) - Queued up files, ready for the next commit which push them to the local git repository 
  3. Git Local Repository - in a `/.git` folder holds all of the git files and histories
  4. Github External Repository
- Branches - `master` is the default branch

## Commands Explained

**`$ git push origin master`**
- `git` - Using the program git
- `push` - Command to send changes to github
- `origin` - Something to do with the name of the github repo
- `master` - The branch you are pushing

**`$ git add`** - Add files to index (staging area)
- `$ git add .` - Recursively add all files to index

**`$ git commit -m "commit message"`** - Commits stages files
- `$ git commit -am "commit message"` - Stages any changed files and then commits in one step. Good for simple changes

**`$ git ls-files`** - List all files currently being tracked in the repo

## Command Line Commands
`$ ls` - Lists all files in working directory
- `-a` - shows hidden files too
- `-l` - shows a long list of files
- `-R` - shows folders recursively
- `-h` - shows files sizes in human readable format 

`$ unzip path/to/zip/file.zip` - Unzips file to working directory