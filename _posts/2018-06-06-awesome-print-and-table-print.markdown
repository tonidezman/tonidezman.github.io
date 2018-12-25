---
layout: post
title:  "Awesome print and Table print gems"
date:   2018-06-06 09:00:00 +0200
categories: rails
---

TL;DR:
  - awesome_print and table_print gems are great tools for enhancing your `rails console` experience

Go to your Gemfile and add this two lines.
{% highlight ruby %}
gem 'awesome_print'
gem 'table_print'
{% endhighlight %}
This gives you `ap` and `tp` methods inside your rails console.

In newer rails versions (Rails v5 and above) the awesome_print is probably an
overkill. Example output using Rails 5.2
{% highlight zsh %}
pry(main)> Task.first
=> #<Task:0x00007fc450adf8b0
 id: 103,
 name: "Task 0",
 project_id: 3,
 created_at: Tue, 25 Dec 2018 11:35:49 UTC +00:00,
 updated_at: Tue, 25 Dec 2018 11:35:49 UTC +00:00,
 complete: true>
{% endhighlight %}

Example output using awesome_print
{% highlight zsh %}
pry(main)> ap Task.first
#<Task:0x00007fc4505a2690> {
            :id => 103,
          :name => "Task 0",
    :project_id => 3,
    :created_at => Tue, 25 Dec 2018 11:35:49 UTC +00:00,
    :updated_at => Tue, 25 Dec 2018 11:35:49 UTC +00:00,
      :complete => true
}
{% endhighlight %}

Example output of table_print gem. Note that you could call `tp Task.first(5)` without column names.
{% highlight zsh %}
pry(main)> tp Task.first(5), :id, :name, :project_id, :complete
ID  | NAME   | PROJECT_ID | COMPLETE
----|--------|------------|---------
103 | Task 0 | 3          | true
104 | Task 1 | 3          | true
105 | Task 2 | 3          | true
106 | Task 3 | 3          | true
107 | Task 4 | 3          | true
=> 0.00097
{% endhighlight %}
