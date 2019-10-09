---
layout: post
title:  "Evergreen Railscasts episodes"
date:   2018-01-01 09:00:00 +0200
categories: Rails
---

All RailsCasts videos are free. I have written a [script](https://github.com/tonidezman/railscast_downloader) that downloads all the episodes

I am going through Railscasts in 2019 and this is my list of episodes I think that you could benefit from even if they are ancient in internet years.

TL;DR:
  - list of episodes with comments with my thoughts why they are still relevant is on the bottom of this page

  <br>

When I started my career in software development as a hobby railscasts was on the peek. But soon right after Ryan Bates took a long vacation from making screencasts and never got back. Sure we got great screencasts like Go Rails, Ruby Tapas and Drifting Ruby but I want to see if there are any relevant Railscasts tutorials for modern Rails.

Over the last few years I heard a lot of people still talking about Railscasts as a resource that helped them tremendously with their leveling up. I want to see for myself what all the buzz is about. By going through the first 50 episodes I found out that even if the episodes are from 2007 there are quite few ones that are still applicable today. Sure the code from Rails version 1 to current 6 is different but this is expected. What strike me is that the fundamentals are the same.

When you go through suggested episodes I suggest you install the latest Ruby and Rails version and code along or if you are like me I first watch the episode and try to implement the exercise myself. Use api.rubyonrails.org and guides.rubyonrails.org as reference.

If you are complete beginner I suggest you first go through [rails tutorial](https://www.railstutorial.org/book) before watching and coding along with Railscasts.

Of course not every episode has aged well so that is why I decided that I will create this blog post and try to distill useful Railscasts episodes for you.

### Evergreen episodes:
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

- **Episode 10, 11, 12**: [Refactoring User Name](http://railscasts.com/episodes/10-refactoring-user-name-part-1?view=asciicast). Nice intro to Refactoring. The practice of Refactoring with test is basicaly the same today at it was then.

- **Episode 13**: [Dangers of Model in Session](http://railscasts.com/episodes/13-dangers-of-model-in-session?view=asciicast). This is basic stuff but for someone just starting please never save object into a session cookie. If you want to do this you better have good reason for doing this. Instead of storing the whole object you should store the id.

- **Episode 14**: [Performing Calculations on Models](http://railscasts.com/episodes/14-performing-calculations-on-models). The code is outdated but you should still add `pry-rails` to your Gemfile and run `bundle install`. Then you can fire `bin/rails console` and look at different methods that you have on your models and look at the SQL that ActiveRecord produces for you.
{% highlight zsh %}
pry(main)> ls Product
Object.methods: yaml_tag
ActiveRecord::Querying#methods:
  any?          eager_load       find_or_create_by      forty_two!  joins             merge    preload          select          update_all
  average       except           find_or_create_by!     fourth      last              minimum  readonly         sum             where
  calculate     exists?          find_or_initialize_by  fourth!     last!             none     references       take
  count         extending        first                  from        left_joins        none?    reorder          take!
  count_by_sql  fifth            first!                 group       left_outer_joins  offset   rewhere          third
  create_with   fifth!           first_or_create        having      limit             one?     second           third!
  delete_all    find_by_sql      first_or_create!       ids         lock              or       second!          third_to_last
  destroy_all   find_each        first_or_initialize    in_batches  many?             order    second_to_last   third_to_last!
  distinct      find_in_batches  forty_two              includes    maximum           pluck    second_to_last!  unscope
{% endhighlight %}

- **Episode 16**: [Virtual Attributes](http://railscasts.com/episodes/16-virtual-attributes). Creating virtual attribute is the same in newer Rails versions.

- **Episode 17**: [HABTM Checkboxes](http://railscasts.com/episodes/17-habtm-checkboxes). The code is outdated but the main takeaway from this episode is that you need to add brackets at the end to like this `product[category_ids][]` tell rails that it should build array for you. Newer Rails have form_with syntax that you can checkout in api.rubyonrails.org how to use.

- **Episode 19**: [Where Administration Goes](http://railscasts.com/episodes/19-where-administration-goes?view=asciicast). Ryan present different approact to admin dashboards. You can embed edit/destroy links right into the page.

# I finished episode 19
- **Episode 0**: [xx](xx).
