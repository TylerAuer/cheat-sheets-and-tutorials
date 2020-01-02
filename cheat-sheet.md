# **Cheat Sheet**

## Table of Contents

- [Command Line](#Command-Line-/-Terminal)
- [Git](#Git)

## **Command Line / Terminal**

### Keyboard Shortcuts

- <kbd>TAB</kbd> - Attempts to autocomplete the directory or file name you are typing. If there are >1 files that fit the letters you have typed, will display all matching files / folders
- <kbd>⇧</kbd> - Cycles through your most recent commands. Useful when running scripts repeatedly during testing or debugging.
- <kbd>CTRL</kbd>+<kbd>C</kbd> - Aborts any running command.

### Moving Around

When working in the command line, you are always somewhere in the file system of your computer. Accessing files means ***moving*** to their location in your file system.

- `pwd` - Shows your current directory
- `ls` - Lists the files in the current directory
- `ls -la` - Lists files ***and*** hidden files in the current directory
- `cd` - Return to home directory
- `cd <subfolder name>` - Navigate to a child directory -- deeper in the file tree
- `cd <subfolder name>/<subsubfolder name>` - Navigate to a child of a child's directory
- `cd ..` - Move to the parent directory -- one level higher in the file tree
- `cd ../..` - Move to the parent of the parent directory -- two levels higher in the file tree

### Changing Files and Folders

- `touch <filename.ext>` - Creates a file with the chosen name and extenstion
- `open <filename.ext>` - Opens a file
- `mkdir <folder name>` - Creates a new folder
- `rmdir <folder name>` - Removes and ***empty*** folder
- `rm -R <folder name>` - Removes folder ***AND*** contents

## **Git**

- `git init` - Initialize git in current directory
- `git clone <repo>` - Get a copy of git repo from server (often github) and place it on your computer
- `git add <file / directory>` - Stages changes for a commit
- `git commit -m "message decribing changes"`
