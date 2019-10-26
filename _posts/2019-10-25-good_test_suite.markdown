---
layout: post
title:  "Good test suite"
date:   2019-10-25 09:00:00 +0200
categories: Testing
---

A lot of developers/managers think that code coverage is a measure of good test suite. I think this is good start but it is not enough and in some circumstances it is even dangerous.

After years of writing automated tests and practicing TDD we need to address the issue of inadequate test suites. I have heard somewhere that developer needs to write 2,000 bad tests before he/she starts to write good ones. I probably wrote around 5,000 tests and I think this estimate is on point for me. I had good mentors that helped me along the way and I have read a lot of books on the subject so I think this 2,000 test estimate depends on each individual.

> To write good test suite we need developers that have experience in writing good tests and can mentor others.

What are good tests? To find out what are good tests I would first like to talk about bad tests.
Bad tests are:
 - flaky (non-deterministic) tests
 - fragile tests
 - useless tests

`Flaky tests` sometimes pass and other times fail. The problem with this type of bad tests are that developers loose confidence with the test suite.

`Fragile tests` are tests that fail evan if the application still works as expected. I once worked with developer that liked to write fragile tests. His reasoning was that he likes to put traps inside the code as a reminder in the future. Don't do this. If the application works the tests should pass period.

`Useless tests` are probably the most common. There is simple cure to avoid writing useless tests.

> When you write tests you need to see the test fail. Then you write the code that fixes the test.

I have been beaten in the past when I wrote tests without this simple rule. What would happen is that I would write test, watch it pass and then write another test and repeat. Some tests were correct in testing the right thing but there were other tests that were either passing because of my mistake or weren't actually testing anything.

### Code coverage
Let's talk about code coverage. Don't get me wrong code coverage is good start and you should be doing it. But what is wrong is thinking that 100% code coverage means that you have good test suite.

Let's look at some code
```ruby
if something && something_else || other_thing
  do_something
end
```

If you write test that `something is true` you will have 100% code coverage but you missed a lot of other corner cases. This kinda test suite is worse than having no tests at all. Because without test suite you at least know that you are not safe.

To combat this issue you could either think about what tests you need to write and/or try mutation testing.

I would encourage you to try mutation testing. You could do mutation testing manually by changing code and run tests. If your change did not brake the test suite you know that you need to write test to catch this mutation. The other and quicker way of doing mutation testing would be to use mutant gem and run mutation testing automatically. The first time I run the automated mutation testing I was quite surprised what corner cases snuck by my tests.

> Mutation testing is great for improving your test suite and catch any regressions.

Maybe in the future we will get some better practice that we currently have. I just heard about `TCR` which stands for `test && commit || revert` which sounds quite interesting and I will try it in the future.
