---
layout: post
title:  "War stories: 5 years of work deleted"
date:   2019-10-04 09:00:00 +0200
categories: WarStories
---

It is 4 pm and one of my coworkers lets call him Timmy stands up and asks other coworker: "Hey did you do anything with our databases today?" The answers was no. Than Timmy asked this question to other coworkers and the answer was always no.

Later I found out that all the database tables were empty. My reaction was that this is no problem we can just rollback the database to the previous snapshot and what I got back from Timmy was something that floored me. Timmy responded that we don't have any database backups.

Instead of Timmy telling everyone that all the database table were truncated he started with the blame game. Maybe he would feel much better if this was not his doing. I don't think this is a right approach. If I reflect on my self I never try to blame people of doing stuff I always try to improve the process so that this doesn't or at least rarely happens again.

If we go back to the story. After hearing that we don't have backups I asked Timmy how could we restore the database. Timmy responded with I don't know. Later we restored the database from logs but his answer revealed how competent Timmy is at his job.

Database restoration from logs would give us 90% of the data back. The problem here was that there was a lot of manual work lost and there were also some things that were done to the data that were not in the logs. So this 90% could wel be 70% or 80%.

Lets find out how we got to this place. Timmy is not the only one in the database team. The is also the architect. This architect had an idea that got us in this mess. Because they wanted to write tests this architect had wanted to run tests on production data. When I first heard this I try to explained to him why this is a bad idea. He explained that he knows what he is doing and that they would have few fail safes that would prevent from tests truncating the data.

As you would probably think this fail safes were not perfect and the data was lost. I pointed out how Timmy's reaction and now lets look at the architect's reaction. He the testing. He said: "If we wouldn't have tests this wouldn't have happened". This was probably just a response that should be probably kept from himself because our team is full of smart and talented developers and they know BS when they see one.

The problem here is that this guy apparently doesn't know that the backup should be done a long time ago and it should be done periodically. Because even if we didn't have this weird test suite running on the production data there is also a chance of disk failures. The author of "Designing Data-Intensive Applications" did a good job of scaring the hell out of me when it comes to disk failures on cloud service provider.
