---
layout: post
title:  "Symbol to Proc"
date:   2018-12-24 09:00:00 +0200
categories: ruby
---

TL;DR:
  - Symbol to Proc is Awesome!
  - You can use it as a shorthand `array.each(&:method_name)`

Lets say we have array of names and we want to transform the names to upcase. One way to do this is to use the map method.
{% highlight ruby %}
arr = %w(toni dare johnny tomaz)

arr = arr.map do |name|
  name.upcase
end

p arr

# >> ["TONI", "DARE", "JOHNNY", "TOMAZ"]
{% endhighlight %}

You could shorten this by using symbol to proc. Let just look at the code and than see what is happening under the hood.
{% highlight ruby %}
arr = %w(toni dare johnny tomaz)
arr = arr.map(&:upcase)

p arr

# >> ["TONI", "DARE", "JOHNNY", "TOMAZ"]
{% endhighlight %}
`:upcase` is a symbol and when we ad `&` infront of the symbol the `.to_proc` method is called on the symbol.

Knowing this we can play around and monkey patch the Symbol class.
{% highlight ruby %}
class Symbol
  def to_proc
    Proc.new { "Joe" }
  end
end


arr = %w(toni dare johnny tomaz)
arr = arr.map(&:upcase)

p arr

# >> ["Joe", "Joe", "Joe", "Joe"]
{% endhighlight %}

If we wanted to reimplement rubys default behaviour we could write the code something like this
{% highlight ruby %}
class Symbol
  def to_proc
    # self is :upcase
    # we are sending message :upcase to a string object
    # this is the same as "joe".upcase
    -> (name) { name.send(self) }
  end
end


arr = %w(toni dare johnny tomaz)
arr = arr.map(&:upcase)

p arr

# >> ["TONI", "DARE", "JOHNNY", "TOMAZ"]
{% endhighlight %}
