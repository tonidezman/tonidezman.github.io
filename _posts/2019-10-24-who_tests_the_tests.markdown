---
layout: post
title:  "The code is tested by tests. But who tests the tests?"
date:   2019-10-24 09:00:00 +0200
categories: Testing
---

TLDR;
> Tests are testing your code and the code is testing your tests.

Quite a while ago somebody made a comment at the meetup that: "test suite is testing the code, but who is testing the tests".

I am writing this blog post to combat scaling issue of explaining this subject to numerous people.

I like to compare this subject to double-entry bookkeeping. Every entry to an account requires a corresponding and opposite entry to a different account. The double-entry has two equal and corresponding sides known as debit and credit. The left-hand side is debit and right-hand side is credit. What is important here to note is that left and right side needs to be the same. If they are not something is not right. The accountant or the person reviewing the document doesn't know which side is wrong but we at least have a methodology that can catch errors.

When you write automated tests you have similar thing happening. When the test fails you don't know if the test is responsible for the breakage or if the code is to blame. What we do know is that something is wrong and we need to fix it.

We could say that:
> "Tests are testing your code and the code is testing your tests."

With this statement I am not saying that every test is a good test. I had a lot of painful experiences working with flaky (non-deterministic) and fragile tests.

What you as a developer should aspire to do/have is a good test suite that has your back. Meaning that when the tests are green you know that most if not all the business logic works as expected.
