---
layout: post
title:  "URL transformation with bookmarks"
date:   2020-01-10 09:00:00 +0200
categories: Tip
---

You have a bug in production and you want to reproduce it on your local machine. Let's say you have url that looks something like this `https://my_app.com/some_path?myQueryString=7`. Normally you would use your mouse and keyboard to change url from current to localhost.

But what if I told you that you don't have to do that anymore. Your production url can be transformed just by a click of a button.

In order to accomplish this we can create bookmark that has url content like this
```javascript
javascript:window.location=window.location.toString().replace(/%5Ehttps:%5C/%5C/(staging\.|beta\.)?myapp.com/,'http://localhost:3000').replace(/%5Ehttps:%5C/%5C/my.second.app.com/,'http://localhost:3001')
```

You can save this link as a bookmark `ToLocalhost` on your favorite browser.
