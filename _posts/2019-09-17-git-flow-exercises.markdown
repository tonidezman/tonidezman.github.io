---
layout: post
title:  "Git-flow Exercises"
date:   2019-09-17 09:00:00 +0200
categories: Exercises
---

Inspired by Julia Evans's [exercises](https://jvns.ca/blog/2019/08/27/curl-exercises/) I created this git-flow exercises to gain the muscle memory and understanding how the workflow of working on features, releases, hotfixes work. Note that these exercises are repetitive on purpose. You should do this exercises 3 days in a row and one more time after a week.

Before doing the exercises you should read the [git-flow concept](https://nvie.com/posts/a-successful-git-branching-model/) and [install](https://danielkummer.GitHub.io/git-flow-cheatsheet/) git flow on macOS, Linux or Windows.

Let's get started:

1. Create empty directory and run `git init`. Then run `git flow init`
2. Create new repo on GitHub.
3. You are building new feature called first_feature. By creating first_feature.txt file you are done.
4. Create the pull request (make sure that the pull request goes from feature/first_feature => develop branch).
5. Merge this pull request from the GUI (i.e. GitHub).
6. It is time for the second_feature. Create second_feature.txt on the feature branch.
7. Create the pull request.
8. Merge this pull request from the terminal.
9. Release develop branch as 0.1 version.
10. Run `git tag` to see the tag version in the terminal.
11. Check out GitHub releases tags. Why can't you see any releases/tags on GitHub?
12. From terminal push tags to origin master branch `git push --tags` and checkout the releases/tags on GitHub.
13. Your boss comes to you and informs you that we have bug in production because first_feature.txt file is empty. create hotfix and add text "bug fixed" to the first_feature.txt file.
14. create and merge the pull request through GitHub (remember: if you don't use git-flow tool you need to manually merge the the code to develop/master branch.)
15. Release this code as 0.1.1 version.
16. You have to fix an urgent BUG. No time for pull request. Add 'squashing bug' text to second_feature.txt and immediately merge the hotfix branch to master. Make sure that you bump up the patch version to 0.1.2
17. You have one massive feature that you will be working right now. Create two new files.
18. Prepare the release as version 1.0 but don't merge the release to the master yet.
19. We have another bug that needs you to delete one file of your choosing.
20. Finally you can release version 1.0 🎉

<br>
<strong>Bonus exercises:</strong>
- Develop new feature while you have release branch open.
- On which branch does git flow tool merge the hotfix code if we have release branch open. What about if we don't have release branch.
- Cleanup branches locally and on GitHub. You should only have master and develop at the end.

<br>
> * throughout exercises you should checkout branches on the GitHub. You should also check the content of the files and ask yourself if the content on the branch that you are looking is what you expect.
> * run `git log --oneline --decorate --graph` to see what is going on.
> * If you are using zsh you can install plugin for git-flow.
