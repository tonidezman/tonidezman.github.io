---
layout: post
title:  "Where is this method comming from?"
date:   2019-04-02 09:00:00 +0200
categories: Ruby
---

{% highlight ruby %}
class Person
end

Person.ancestors # => [Person, Object, Kernel, BasicObject]
{% endhighlight %}

Do you know where `ancestors` method is coming from? I don't either so let's investigate.

We know that the lookup chain contains `[Person, Object, Kernel, BasicObject]` so lets start here.
{% highlight ruby %}
result = Person.ancestors.select do |class_or_module|
  class_or_module.instance_methods(false).include?(:ancestors) || el.methods(false).include?(:ancestors)
end

result # => []
{% endhighlight %}

This is weird. It looks like that those Classes and Kernel Module don't contain `ancestors` method. We are probably doing something wrong here. Lets' examine this a little more.

{% highlight ruby %}
# Ok we are calling
Person.ancestors

# We know that Person is a Class.
Person.class # => Class

# Lets see if the ancestors method is inside Class.
Class.instance_methods(false).include?(:ancestors) # => false
Class.methods(false).include?(:ancestors) # => false

# Oh man. Well this is disappointing.
# Lets look what ancestors does Class have.
Class.ancestors # => [Class, Module, Object, Kernel, BasicObject]

# Oh wait. Do you see the difference here between Person and
# Class method lookup chain. It has a Module.
Module.instance_methods(false).include?(:ancestors) # => true
Module.methods(false).include?(:ancestors) # => false
{% endhighlight %}

Yes. We did it! We found it inside Module.
