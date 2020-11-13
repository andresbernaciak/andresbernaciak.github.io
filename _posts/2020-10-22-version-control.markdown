---
layout: post
title:  "What is version control?"
date:   2020-10-22 21:03:36 +0530
categories: git
---

## Definition
In simple terms, version control is a methodology used to track changes in a file. For those who have used the "track changes" button in MS Word, this might seem familiar, though version control systems (VCS) have added functionalities including the ability to handle multiple users editing the same file simulatenously, which is something very common in this time and age.
'Git' is one of the version control systems out there, and it is usually used in conjunction with GitHub with is a cloud-based hosting service that lets you manage Git repositories (think folders to save your projects that sync up to your google drive).

## How does version control systems work
There are a ton of tutorials online that will do a much better job than I can at teaching you about stagging, commits, checkouts, push, forks, branches and so on.  Here's a short list of some I found useful:

* [Github Tutorial For Begginers](https://youtu.be/0fKg7e37bQE)
* [Arch Wiki: Git](https://wiki.archlinux.org/index.php/git)


## Installation and usage
Head over to [www.git-scm.com/downloads](https://www.git-scm.com/downloads) and download the version for your OS.


## The most common commands I'll be using

Make sure you are running these on a terminal (Git Bash on Windows).


```
git init  # to initialize a repository (you only do this once)

git add . # adds all working files to the stagging area

git commit -m "comment"  # commits changes and includes commentary

git push   # upload to github (requires setting the user and email using "git config --global user.name and user.email)
```



