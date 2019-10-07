---
layout: post
title:  "How not to do System tests"
date:   2019-10-04 09:00:00 +0200
categories: WarStories
---

I hope that I don't have to convince you the benefit of having good test suite that you can rely on. It is a great feeling when you develop new feature run tests and know that your app works as it should.

Little over a year ago I started to work on a project that had test suite but no one was using it and it has not been run by developers in years.

One year has past and we now have over 700 tests. The team is writing unit and integration tests and we even started to think how we could have System test meaning few tests that would check if the whole system works.

> You should be able to run system tests locally. Don't create separate server just for system tests.

We had weird deployment pipeline and some code would have to be fixed before we could run system tests locally. We decided to create system test server and create separate repo that would use selenium (capybara) which would do some white box tests but mostly black box testing through the whole system. I was convinced in doing this because we didn't have time to fix deployment and legacy code and I didn't yet have good reasons why this is a bad idea. But now that I have gone through the process I know better. I also know how to convince stakeholder in fixing technical dept first before continuing.

### Pain points
When you have System test server only one person can use it. This brings pain and you need to coordinate who can use it and at what time. We used separate slack channel and hooks to inform others that I am using system test server. When you have few people working on the app this could be ok but when more people use this server you will feel the pain. This would have been avoided if we would be abele to run tests locally.

I had an interesting day when one other coworker was running tests when I was trying to figure out why we have some flaky (non deterministic) tests. I asked the team if anyone is running the tests and I got answer from everyone that they are not running any system tests. Later I found out that one of my coworkers was mistaken in that he wasn't running just one subset of system tests that would take 20 minutes but was running the whole test suite that took 3 hours.

In the GOOS book (Growing Object Oriented Software) the authors say that is important to have CI/CD pipeline at the beginning of the project. I agree with Freeman and Pryce. If you have project that will last for more than few weeks you should start with building the CI pipeline and the whole process of adding new or changing existing features will be much more enjoyable.

When doing the system tests or any fixup, refactoring etc. Try to come up with as many solutions as possible and then choose the right one for your circumstances. We are always learning new things and making mistakes is inevitable. Try to learn as much as you can from others and share your war stories so that others can learn from your insights.
