---
layout: post
title:  "War stories: Create readonly user"
date:   2019-10-05 09:00:00 +0200
categories: War stories
---

> Having readonly user for production just saved my ass!

Let's start from the beginning. A week earlier I was debugging something and I needed to have a production data to replicate the bug. I changed my app connection to production and to be safe I started my rails console in the sandbox mode so that I would not effect any production data.

I found and fixed the bug. Before fixing the bug I wrote test that would catch the bug. This would also enable us to catch similar bugs in the future. But what is important in this story is that I forgot to switch my database.yaml file back to local database.

Next day I started my rails console and tried to delete a lot of data. But when doing that I got some weird database error that I don't have permissions to do that. From this error I found out that I was lucky that I used database permissions of readonly user.

Instead of wasting a lot of time. There would be a lot of hours in writing up the postmortem and explaining my boss why this happened and why. Time and energy would also be spend on fixing the deleted production data.

But instead of that I was able to continue with my task as nothing had happened.
