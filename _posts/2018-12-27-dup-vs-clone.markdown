---
layout: post
title:  "dup vs clone in Ruby"
date:   2018-12-27 09:00:00 +0200
categories: Ruby
---

TL;DR:
  - clone duplicates everything (including singleton methods, freeze state, etc.)
  - dup duplicates most of the things

Let's create simple Person class one person object with singleton method
{% highlight ruby %}
class Person
  attr_accessor :name
end

person = Person.new
person.name = "Toni"

def person.say_name
  "My name is #{name}"
end

person.say_name # => "My name is Toni"
{% endhighlight %}


Let's se what happens if we try to access singleton person method with dup or clone
{% highlight ruby %}
class Person
  attr_accessor :name
end

person      = Person.new
person.name = "Toni"

def person.say_name
  "My name is #{name}"
end

cloned_person = person.clone
dup_person    = person.dup
cloned_person.say_name # => "My name is Toni"
dup_person.say_name    # => NoMethodError: undefined method `say_name'
{% endhighlight %}
We just found the first difference between dup and clone.

Let's also freeze the person before duplicating the object and see what happens.
{% highlight ruby %}
class Person
  attr_accessor :name
end

person             = Person.new
person.name        = "Toni"
person.freeze
cloned_person      = person.clone
dup_person         = person.dup
dup_person.name    = "Joe"
cloned_person.name = "Joe" # ~> FrozenError: can't modify frozen Person
{% endhighlight %}

The best thing to remember the difference betwen dup and clone is that dup is a "shallow" copy and clone make almost exact copy fo the object.
