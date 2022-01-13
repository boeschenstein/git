# GIT

> GIT Information and Hints

## Strategies/Workflows

### Branch strategy "GitLab Flow"

It is a simple branch strategy and good for smaller developer team: <https://about.gitlab.com/topics/version-control/what-is-gitlab-flow/>. 

### The top six Git workflows to strengthen software development

1. Centralized Git workflow
2. Feature branching Git workflow
3. Trunk-based development Git workflow
4. Personal branching Git workflow
5. Forking Git workflow
6. GitFlow Git workflow

Source: <https://about.gitlab.com/topics/version-control/what-is-git-workflow/>

## Git Client: "Git Extensions"

Silly name, but free and Open Source and no account required: http://gitextensions.github.io/

## Git Credential Manager Core

Version v2.29.0 upgrades existing users of [Git Credential Manager for Windows](https://github.com/microsoft/Git-Credential-Manager-for-Windows/) (which was just deprecated) to [Git Credential Manager Core](https://github.com/microsoft/Git-Credential-Manager-Core) ("GCM Core", which is the designated successor of the former).

## Examples

### Status

`git status`

### New repo

`git init .`\
`git init --bare /path/to/repo.git`
	Central repositories should always be bare repositories (they shouldn’t have a working directory)

### Show branches

`git branch`     shows all changes, master == "trunk"\
`git branch -v`  shows last changes\
`git branch -r` remote only\
`git branch -a` local only\
`git branch --merged` or `-- no-merged`

### Branch

`get branch <name>`  new branch, f.e. "hotfix"\
`git checkout <name>` switch to branch\
`git checkout -b <name>` create and switch to new branch\
`git branch -d <branch>` delete any temporary branches, f.e. "hotfix"\
`git checkout HEAD <file>` Discards changes in the working directory (to latest of branch???)

### Stage

`git add <file>`   stage new or existing file\
`git commit -m "my comment"` works after stage - GEHT NIE ????\
`git commit -a -m "my comment"` -a: all -m: message\
`git reset HEAD <filename>` unstage a file - file content doest not change\
`git reset <first 7 letters of SHA>`\
	- undo last steps
	- Can be used to reset to a previous commit in your commit history
	- show log to get SHAs

### Merge

`git merge <from-branch>` from target (f.e.master) branch: get data from <from-branch> f.e. "hotfix"\
`git merge origin/master`\
`git mergetool` starts merge

### Clone (continue on existing work from others/git server)

`git clone <url>`	Creates the same subfolder as on git server

### Work with remote git (origin = alias for remote url or path)

`git remote -v` or `git remote show` or `git ls-remote`: shows where origin points to\
`git remote add <remote_alias> <url>`\
`git remote add origin https://fabrikam.visualstudio.com/Fabrikam/_git/FabrikamFiber`

`git fetch or git fetch <remote_alias>` get data --> source is called origin\
  needs usually following statement to get the files: (merge this work in your branch)\
    `git checkout -b <new_local_branch> <remote_alias>/<new_local_branch>`\
  or merge in existing branch:\
    `git merge <remote_alias>/<current_local_branch>`
    
`git push <remote_alias> <your_branch>` store data to remote branch\
`git push origin master`\
`git push --all origin` pushes all local branches in one go
	
`git clone -o <url or path>` creates alias 'origin' for remote url or path
	
`git pull` update local files with git server files\
`git pull --rebase origin master` you can do this after git push failed due to conflict\
  -> check the differences now in all files !! comments like this added: <<<<<<< HEAD
	
### Remove a file (stage?? branch??)

`git rm <file>`

### Differences

`git diff <filename>`

### History

`git log`\
`git show HEAD`

## Migration tool TFS -> git

https://github.com/git-tfs/git-tfs

>BEWARE: we had issues with git-tfs: please check all relevant branches and do a full compare 
	
(we lost all new files and file deletions in the last branch created a day before)

## Links

- Documentation: https://git-scm.com/doc
- Most common workflows: https://www.atlassian.com/git/tutorials/comparing-workflows 
- https://ohshitgit.com/
- https://github.com/git/git/
- Migration tool TFS -> git: https://github.com/git-tfs/git-tfs
