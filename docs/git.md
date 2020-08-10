---
layout: page
title: Git
permalink: /git
---
---

## Basic

| Command | Description |
| ------ | ------ |
|`git status`|Gets the status of the repo|
|`git pull`|git fetch + git merge|
|`git fetch origin [branch]`||
|`git checkout --track origin/[branch]`|When a remote branch needs to be checked out and tracked|

---

## Staging

| Command | Description |
| ------ | ------ |
|`git add -A`|   stages All|
|`git add .`|    stages new and modified, without deleted|
|`git add -u`|   stages modified and deleted, without new|
|`git checkout`| Reverting  / Unstage|

---

## BRANCHING

##### Basic branching

| Command | Description |
| ------ | ------ |
|`git branch` | Shows current branch|
|`git branch -a`| Shows all the branches|
|`git checkout [foo]`| Will change current branch to foo|
|`git checkout -b [foo]`| Will create a new branch foo|
|`git branch --contains <commit_hash>`|Only list (local) branches which contain the specified commit|
|`git branch -r --contains <commit_hash>`|List (remote) branches which contain the specified commit|

##### Delete Branch

| Command | Description |
| ------ | ------ |
|`git branch -d <branch_name>`|  Delete local branch|
|`git push origin --delete <branch_name>`| delete remote branch on server|

##### Remove Stale Branch (when a branch is removed from remote but exists in the local remote-tracking branch)

| Command | Description |
| ------ | ------ |
|`git remote prune origin`| Removes all stale branches|
|`git branch -d -r origin/stale_branch`|Removes a specific branch|

##### Merge Branch

| Command | Description |
| ------ | ------ |
|`git merge [some_other_branch]`|Will merge [some_other_branch] to the current branch|

##### UNDO MERGE NOT YET PUSHED

| Command | Description |
| ------ | ------ |
|`git merge --abort`|Will roll back all merges, if COMMIT has NOT been called|
|`git reset --hard Commit_hash_SHA`| Will roll back to previous commit, if changes have been COMMITED|
|`git reset --hard HEAD~1`|Will get you back 1 commit.

##### UNDO Merge that has been PUSHED

| Command | Description |
| ------ | ------ |
|`git revert -m 1 Commit_hash_SHA`|To undo a merge that was already pushed|

##### UNDO A COMMIT AND REDO

```git
$ git commit -m "Something was incorrectly commited"
$ git reset HEAD~
<< edit files as necessary >>
$ git add
$ git commit -c ORIG_HEAD
```

---

## DIFF and MERGE tools

| Command | Description |
| ------ | ------ |
|`git diff` or `git difftool`| Will display differences|
|`git mergetool`|This will fireup the mergetool (kdiff3) or another other configured|
|`git clean`| Remove *.orig files left by a merge|

---

## Rebase

##### Strategy 1 - Without using rebase or merge squash

The count here (HEAD~3) works just like in Vim. eg. Yank 3 lines would include the current line and two more lines.  
If you wan to Write your own commit message

```git
git reset --soft HEAD~3 &&
git commit
```

If you want to reuse all commit messages from the squashed commits

```git
git reset --soft HEAD~3 && 
git commit --edit -m"$(git log --format=%B --reverse HEAD..HEAD@{1})"
```

---

## GRAPH

```git
git log --graph --oneline --decorate --all
or
git log --graph --abbrev-commit --decorate --date=relative --all
```

---

## CONFIG

| Command | Description |
| ------ | ------ |
|`git remote show origin`| Shows the origin |
|`git remote add origin <URL>`| Point the current repository to a remote repository|
|`git remote -v`| List the fetch and push URLs of the remote repository|
|`git config --list`| List the configuration of the current repo , includes [--local|--global|--system]|
|`git config --list --show-origin`| Can be used with [--local|--global|--system]|

Git will use Local/System/Global in that order, based on availability of key values.

```git
git config --local user.name "Foo"
git config --local user.email "Foo@foo.com"
git config --system user.email "Foo@foo.com"
git config --global user.email "Foo@foo.com"
```

---

## Credentials

| Command | Description |
| ------ | ------ |
|`git config credential.helper cache`| Used in Linux Systems - will cache the password in memory|
|`git config credential.helper 'cache --timeout 7200'`|  Cache password in memory for 7200 seconds|

---
