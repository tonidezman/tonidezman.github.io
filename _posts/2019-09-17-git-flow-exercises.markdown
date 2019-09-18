---
layout: post
title:  "Git-flow Exercises"
date:   2019-09-17 09:00:00 +0200
categories: exercises
---

Inspired by Julia Evans's [exercises](https://jvns.ca/blog/2019/08/27/curl-exercises/) I created this git-flow exercises to gain the muscle memory and understanding how the workflow of working on features, releases, hotfixes work. Note that these exercises are repetitive on purpose. You should do this exercises 3 days in a row and one more time after a week.

Before doing the exercises you should read the [git-flow concept](https://nvie.com/posts/a-successful-git-branching-model/) and [install](https://danielkummer.github.io/git-flow-cheatsheet/) git flow on macOS, Linux or Windows.

Let's get started:

1. Create empty directory and run `git init`. then run `git flow init`
2. You are building new feature called my_feature. By creating great_feature.txt file you are done.
3. Release this feature as 0.1 version.
4. Your boss comes to you and informs you that we have bug in production because great_feature.txt file is empty. create hotfix and add text "bug fixed".
5. Release this code as 0.1.1 version.
6. You have one massive feature that you will be working right now. create two new files.
7. Prepare the release as version 1.0 but don't merge the release to the master yet.
8. We have another bug that needs you to delete one of the files that you generated in the release branch.
9. You can release the branch as 1.0.1
