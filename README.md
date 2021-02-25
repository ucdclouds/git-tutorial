# Github tutorial
## First steps

* Make sure git is installed
    * SSH keys for those who want them

* Git config
    * `git config --global user.name "Name"`
    * `git config --global user.email "user@email.com"`
    * Editor 
        
        * `$EDITOR` or `$VISUAL` [System Wide]
            * e.g. `export EDITOR=vim` in `~/.bashrc`
        * `git config --global core.editor vim/emacs/etc` [Git only]

## Most important commands to remember
* `git status` -- shows current status, including which files are tracked/untracked and which are staged
* `git log` -- Shows a log of all commits. 
    * By default, this is hard to read. I personally have `alias lg="git log --all --decorate --oneline --graph"` specified in my `.bashrc`, so all I need to type is `lg` for a more readable git log
* `git add` -- add (stages) file
* `git commit` -- Commits all staged files
* `git push` -- pushes all commits to remote repository
   * `git pull` -- pulls commits from remote repository

## Create your first repository

* Starting from command line:
    * `git init` -- Sets up git repository in current folder
    <!-- * `git add <filename>` -- Single File (also accepts wildcars like `./*.py`) -->
    * Add remote repository
        * `git remote add <name> <url>`
        * `<name>` can be any name, typically the main remote branch is called `origin`
        * `<url>` is the URL of the git repo. This looks like `https://github.com/<username>/<repo_name>` if using HTTPS and `git@github.com:<username>/<repo_name>.git` if using SSH.
* Starting from web
    * Create repository on GitHub.com (or equivalent)
    * Clone repository
        * `git clone https://github.com/<username>/<repo_name>` -- HTTPS/no SSH
        * `git clone git@github.com:<username>/<repo_name>.git` -- SSH
    * Remote repository will automatically be added with this method, with the default name `origin`.

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
    * If the file has been updated since the last `git add` but before a commit, you will need to `git add` the file again. 
        * I generally only stage files immediately before committing so that I know they're all at the latest version

_Note: Git will continue to stage the file, even if it's deleted. If a staged file is deleted, you will need to `git add <filename>` it again to make git aware of its deletion_

* Commit the files
    * `git commit` -- Opens a text editor (set via `git config`) to write commit message on the top line. Save the file and quit the editor to continue the commit process.
        * Alternatively, `git commit -m "<message>"` bypasses the editor entirely

## Branches
 __This section may be incomplete in time for the Git workshop on Feb 25th.__

Branches are very powerful, but may not be necessary if you're just using Git to keep your code backed up. A good usecase for branches are 
1) if you're making a change that would potentially break `master`, and you want to keep `master` "clean" as the working version or 
2) if you're contributing to someone elses repository

### Creating branches
* `git checkout -b <branch_name>`
    * This is short for `git branch <branch_name>` and `git checkout <branch_name>`, so it creates and checks out a new branch
        * By default, this branch is identical to wherever `HEAD` is (`HEAD` is git-speak for what is currently checked out. This could be an old commit, a branch, etc). Unless you have specified otherwise, `HEAD` is at the latest commit of the current branch.
* Now there are two branches, one `master` (by default) and the second `<branch_name>`. 
    * Switch between the two with `git checkout master`, `git checkout <branch_name>`
* The two branches are completely isolated from each other. Changes to one branch do not affect the other 

### Merging
Often, you're going to eventually want to merge the contents of one branch into the other.
* `git merge <branch_name>` will merge all changes from `<branch_name>` _into the current branch._
    * Git __always__ merges the specified branch __into__ the current checked-out branch.
* Git will automatically detect any conflicts between the two versions. Often, it's able to reconcile the differences on its own but sometimes it requires some manual intervention.

## Diff
Much like the command `diff`, `git diff` can provide information on the differences between files in different commits. 

* By default, `git diff` alone will show the changes between all _unstaged_ and the _last commit_. 
    * `git diff --staged` shows changes between _staged_ and _last commit_
* You can also see the differences between two versions of a file, using the commit hash found by running `git log`
    * e.g. `git diff db821bc 5104f19 my_file.txt` where the two commit hashes are the shorter versions given by `git log --oneline`           
* `git diff <branch1> <branch2>` see diff between branches                        

## Working with remote repositories
 __This section may be incomplete in time for the Git workshop on Feb 25th.__

 Adding and committing files works even if you're not syncing with a remote repository, allowing for a local "track changes" of your code (which can be useful!). However, the power of Git comes from being able to publish your code online and work collaboratively.


 * If you don't have a remote repository set up yet, make sure you go back to that section and do that first
 * Once you have made commit, you can push it online. This can be done with `git push origin master`. This pushes the current commit to the `master` branch of the `origin` remote repository. 
    * You can specify `-u` (`git push -u origin master`) to let git know that this is the "upstream" repository, meaning in the future you only need to `git push` without specifying the branch or repository name.
* Similarly, if there was a change in the remote that you want to pull into your current repository, you can so `git pull origin master` (or `git pull` if `origin master` is set to be the upstream branch).
# External Links
* [Git Online Ebook](https://git-scm.com/book/en/v2) -- Great resource!
* [Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
* [Group Folder](https://github.com/ucdclouds/)
<!-- [Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet.pdf) -->
