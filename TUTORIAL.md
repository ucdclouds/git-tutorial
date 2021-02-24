# Github tutorial
## First steps

* Make sure git is installed
    * SSH keys for those who want them

* Git config
    * `git config --global user.name "Name"`
    * `git config --global user.email "user@email.com"`
    * Editor 
        
        * `$EDITOR` or `$VISUAL` [System Wide]
        * `git config --global core.editor vim/emacs/etc` [Git only]

## Create your first repository

* Starting from command line:
    * `git init` -- Sets up git repository in current folder
    * `git add <filename>` -- Single File (also accepts wildcars like `./*.py`)
* Starting from web
    * Create repository on GitHub.com (or equivalent)
    * Clone repository
        * `git clone https://github.com/<username>/<repo_name>` -- No SSH
        * `git clone git@github.com:<username>/<repo_name>.git` -- SSH

## Adding and committing files
* Check the status of your repository with `git status`
    * Will list untracked files, tracked files with unstaged changes, and staged files
        * Staging = telling git to add the file to the next commit
    
* `git add <file>` -- Stages file to be committed
    * `git add .` -- Stages all files (even those in folders)
    * `git add *.py` -- Only stage `.py` files
    * __Did you accidentally stage a file that you didn't want to?__
        * `git restore --staged <filename>`
        <!-- * `git rm --cached <filename>` also works, but take care to add `--cached` otherwise the file will be completely deleted from the disk -->

_Note: Git will continue to stage the file, even if it's deleted. If a staged file is deleted, you will need to `git add <filename>` it again to make git aware of its deletion_

# External Links
* [Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
* [Group Folder](https://github.com/ucdclouds/)
<!-- [Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet.pdf) -->