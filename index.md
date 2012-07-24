---
layout: default
title: Git Cheat Sheet
---

* the table of contents
{:toc}

# Branches

Branch erstellen

	$ git branch feature-3


Branch erstellen und sofort drauf arbeiten

	$ git branch checkout -b feature-3


Auf Branch wechseln

	$ git checkout feature-3


Remote Branch erstellen

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
