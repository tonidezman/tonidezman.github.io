---
layout: post
title:  "Evergreen Railscasts episodes"
date:   2018-01-01 09:00:00 +0200
categories: Rails
---

## !This is work in progress!

I am going through Railscasts in 2019 and this is my list of episodes I think that you could benefit from even if they are ancient in internet years.

TL;DR:
  - list of episodes with comments with my thoughts why they are still relevant is on the bootom of this page

  <br>

When I started my career in software development as a hobby railscassts was on the peek. But soon right after Ryan Bates took a long vacation from making screencasts and I never got back. Sure we got great screencasts like GoRails, Ruby Tapas and Drifting Ruby but I want to see if there are still relevant tutorials exercises for Rails 6.0 and above.

Over the last few years I heard a lot of people still talking about Railscasts as a resource that helped them tremendously with their leveling up.

By going through the first 50 episodes I found out that even if the episodes are from 2007 there are quite few ones that are still applicable today.

When you go through suggested episodes I suggest you install the latest Ruby and Rails version and code along or if you are like me I first watch the episode and try to implement the exercise myself. Use api.rubyonrails.org and guides.rubyonrails.org as reference.

If you are complete beginner I suggest you first go through [rails tutorial](https://www.railstutorial.org/book) before watching and coding along with Railscasts.

Of course not every episode has not aged well so that is why I decidet that I will create this blog post that will have TLDR with relevant episodes on top and episodes with comment on why I think this episode could be of use to you.

### Evergreen episodes:
- **Episode 0**: [xx](xx). In this episode Ryan explains how to use memoization in Ruby

- **Episode 1**: [Caching with Instance Variables](http://railscasts.com/episodes/1-caching-with-instance-variables?view=asciicast). In this episode Ryan explains how to use memoization in Ruby

- **Episode 4**: [Move Find into Model](http://railscasts.com/episodes/4-move-find-into-model?view=asciicast)
Good episode on how to extract business logic into models. In the modern Rails you can also use scopes
{% highlight ruby %}
class Task < ApplicationRecord
  scope :find_incomplete, -> {where(complete: false).order(created_at: :desc)}
  # ...
{% endhighlight %}
Difference between class methods and scopes is that scopes are always chainable.

- **Episode 6**: [Shortcut Blocks with Symbol to_proc](http://railscasts.com/episodes/6-shortcut-blocks-with-symbol-to-proc). If you want some more information on how to_proc works you can read my [Symbol to Proc](https://tonidezman.github.io/ruby/2018/12/24/symbol-to-proc.html) blog post.

- **Episode 8**: [Layouts and content_for](http://railscasts.com/episodes/8-layouts-and-content-for). It is interesting that code from 2007 works in 2019.

- **Episode 9**: [Filtering Sensitive Logs](http://railscasts.com/episodes/9-filtering-sensitive-logs). Note that rails does this by default but the principles still apply to modern web development. You should not log any sensitive data to your .log files. You can filter out additional sensitive user information in config/initializers/ folder

{% highlight ruby %}
# filter_parameter_logging.rb
Rails.application.config.filter_parameters += [:password]
{% endhighlight %}

{% highlight ruby %}
{% endhighlight %}
