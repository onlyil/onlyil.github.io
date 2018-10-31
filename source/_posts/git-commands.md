---
title: Git Commands Note
date: 2018-10-31 18:30:00
tags: git
icon: fa-git
---

# Git Commands Note

## git merge-base <branch1> <branch2>

Find common ancestor of two branches.

## git commit —amend

A convenient way to modify the most recent commit.

- It lets you combine staged changes with the previous commit instead of creating an entirely new commit.
- It can also be used to simply edit the previous commit message without changing its snapshot.

## git cherry-pick <commitID>

Apply the changes introduced by some existing commits.

## git rebase -i <commitID>

Interactive rebasing gives you the opportunity to alter individual commits. This lets you clean up history by removing, splitting, and altering an existing series of commits.

## git checkout —patch <branch> <file>

Merge other branch some file.

## git checkout <branch> <file>

Copy other branch some file directly.

## Tip

### Resubmit last commit that has been push to remote

``` bash
  git reset HEAD^
  git stash
  git push —force
  git stash pop
  git add .
  ...
```
