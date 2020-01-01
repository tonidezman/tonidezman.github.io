---
layout: post
title:  "URL transformation with bookmarks"
date:   2020-01-01 09:00:00 +0200
categories: Tip
---

You are looking at your production url like `https://my_app/some_path?myQueryString=33+...` and now you want to see how this path is behaving locally. Normally you would use mouse and copy paste this in your favorite browser. This is not that difficult if you have short url but if you have a lot of query string this can become difficult to just copy paste. Before this trick I just copy/pasted the url into my text editor and then copy paste the path back to the new browser tab with `localhost:3000/<paste-path>`

What you can do is to create bookmark with name like `ToLocalhost` and inside url you add the code something like
```javascript
javascript:window.location=window.location.toString().replace(/%5Ehttps:%5C/%5C/(staging\.|beta\.)?myapp.com/,'http://localhost:3000').replace(/%5Ehttps:%5C/%5C/my.second.app.com/,'http://localhost:3001')
```

You can use just one replace if you will be using this link transformation for one app. But if you have multiple apps that you normally use them in the different ports you can use them as descried above.
