---
layout: default
title: Git Cheat Sheet
---

# Table of Contents

* the table of contents
{:toc}

# Repositories

Create a repository

	$ cd MyProject
	$ git init

Clone locally 

	$ git clone /path/to/repo
	
Actually this will clone the repository with hard links, meaning it awesomely fast. If you want
git to copy the repository instead, do it like
	
	$ git clone file://path/to/repo

# Branches

## List Branches

List existing branches

	$ git branch
  	groovy-experimental
	* master
  	sql-table-type

List remote tracking branches

	$ git branch -r
	  default/master
	  github/master

List all branches (and more) on remote

	$ git remote show github
	* remote github
	  Fetch URL: git@github.com:brands4friends/daleq.git
	  Push  URL: git@github.com:brands4friends/daleq.git
	  HEAD branch: master
	  Remote branch:
	    master tracked
	  Local branch configured for 'git pull':
	    master merges with remote master
	  Local ref configured for 'git push':
	    master pushes to master (up to date)

## Working on Branches

Create a local branch

	$ git branch feature-3

Switch to a branch

	$ git checkout feature-3

Creating a new branch and checking it out in one go

	$ git branch checkout -b feature-3

Create a branch locally and push it to a remote repository

	$ git checkout -b feature-3
	$ git push origin feature-3


Branch Löschen

	$ git branch -d feature-3


Remote Branch löschen

	$ git push origin :feature-6

Remote Branch ziehen, der noch nicht lokal existiert

	$ git checkout --track origin/feature-5

mit fetch kommen die aber scheinbar rein, also dann reicht git checkout auch Änderungen in Working Directory zurückrollen.

	$ git checkout -- file

Remote Repository ansehen

	$ git remote show origin

# Serving a Repository

Git Repository serven

	$ git daemon --reuseaddr --verbose --base-path=. --export-all ./.git


Alias dafür bauen

	$ git config --global alias.serve '!git daemon --reuseaddr --verbose --base-path=. --export-all ./.git'

# Analyzing Commits

Incoming Commits von Remote auf einem Branch sehen

	$ git log ..origin/feature-7

also von HEAD bis origin/feature-7

Von remote updaten
Nicht pull automatisch, sondern fetch & merge
Auf dem Branch

	$ git fetch
	$ git merge origin/branch-name

Immer vom upstream mergen, wenn kein branch bei merge angegeben

	$ git config --global merge.defaultToUpstream true


dann halt

	$ git merge
