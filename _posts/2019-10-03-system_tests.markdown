---
layout: post
title:  "War stories: system tests"
date:   2019-10-04 09:00:00 +0200
categories: WarStories
---

I hope that I don't have to convince you to know the benefit of having good test suite that you can rely on. It is a great thing when you develop new feature and run tests knowing that 99% the app works as it should.

When I first join the team. We had some apps that had tests but were not maintained so when I ran them there were a lot of failing tests. And there were other apps that had not test suite at all.

Because you have code that doesn't have your back you implement and ship draft code meaning that you don't refactor it to be more maintainable and easier to understand.

This changed and after a year we have a solid test suite that catches some of the bugs. But we will need quite some time to catch most of the bugs.

Up till know we were writing mostly unit and integration tests. I purposed to our CTO that we need system tests that would test the whole system and would bring us even more confidence.

He give me green light and so I went on making this a reality. The problem was that we have weird deployment system which is not Dockerized and we were on time constraint that we cannot do everything right so what we did is have our own Systemtest server that would enable us to write selenium test that would check for few path that would check if the system is correctly working.

The problem is that only one can run tests at one time. I felt the pain of this when somebody was running tests as well and I had a weird state that because of test setup and teardown my tests would sometimes pass put other times would for some reason fail. I lost hours because of that. Afcourse I asked if anybody was running the tests and the answer was no. The guy doing this was not lying becuase he thought that he was running tests for one country and knew that the runtime was around 30 minutes. But what he was doing was that he run tests for all countries and that took 4 hours.

I was frustraited and our CTO had a great idea that we should have slack channel that we would have postings on Systemtest server timestamps on when the test suite is running and when it stopes as well as I would post that I was creating new tests and I would be using the server for the day.

The whole experience was painful. We should have Dockerized the app and this would not only give us benifits for running the system tests but also for deployment and scalibility.

We should have done this right. There was a lot of technical dept but looking back it would have taken us lot les time to do it right.
