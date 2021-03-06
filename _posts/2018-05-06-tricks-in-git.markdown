---
layout: post
title:  "Tricks in git"
date:   2018-05-06 09:00:00 +0200
categories: Git
---

TL;DR:
 - git pickaxe
 - git add -p (add just specific changes to staging)
 - tig (useful commandline tool)
 - use git aliases to save keystrokes in your .basrc file
 - Octothree (browser extension)

If you are trying to find how code inside the project changed through time you can used so called **git pickaxe**.

{% highlight zsh %}
$ git log -S "some code" --reverse --patch
{% endhighlight %}
What this does is shows you all the commits and its content (oldest commits first).

Cool git command I use regularly is
{% highlight zsh %}
$ git add --patch
# or
$ git add -p
{% endhighlight %}
Which enables you to add specific code to staging and not just the
whole file.

If you want to see what commit changes were made on particular file
{% highlight zsh %}
$ git log -- my_file.txt
{% endhighlight %}
`--` says that this is current branch. You can add `--patch` before `--` to see the changes.

One command line tool I enjoy using is **tig**. I mostly use it
for inspecting commits, commit history, diffs etc.

Because I often use commands like the ones listed below

{% highlight zsh %}
$ git status -s
$ git commit
$ git diff
$ git log --oneline
{% endhighlight %}

To save few keystrokes I added these commands to aliases in my .zshrc file. If you use Bash you can add them to your .bashrc file.


{% highlight zsh %}
alias gs='git status -s'
alias ga='git add '
alias gb='git branch '
alias gc='git commit'
alias gd='git diff'
alias gds='git diff --staged'
alias gp='git push '
alias gpl='git pull '
alias gl='git log --oneline'
{% endhighlight %}

The next trick is not just git specific but I found it so useful
that I want to mention it here. If you use github and miss
navigating the source code in the same way as in your text editor
you can install Octothree. This is browser extension that enables
you to navigate files and folder in a tree like structure.
