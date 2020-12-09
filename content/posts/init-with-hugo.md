---
title: "Init With Hugo"
date: 2020-12-08T19:04:31-03:00
summary: "Let's play with hugo!"
tags: ["hugo", "frameworks", "website"]
draft: false
---

Well, my first real blog, with Hugo.
This post is just to test the framework, I will complement this later.

## Info

| hugo version | Hugo Static Site Generator v0.79.0-1415EFDC linux/amd64 BuildDate: 2020-11-27T09:09:02Z  |
|--|--|
| theme | [PaperMod](https://github.com/adityatelange/hugo-PaperMod/) |

`config.toml`:
```toml
baseURL = "http://mateus.great-site.net/"
title = "Mateus Felipe Gonçalves"
theme = "papermod"

[[menu.main]]
name = "Archive"
url = "archive"
weight = 5

[[menu.main]]
name = "Search"
url = "search/"
weight = 10

[[menu.main]]
name = "Tags"
url = "tags/"
weight = 10

[params.profileMode]
enabled = true
imageUrl = "https://avatars1.githubusercontent.com/u/40613276?v=4"
imageWidth = 120
imageHeight = 120
ShowShareButtons = true
ShowReadingTime = true


[[params.profileMode.buttons]]
name = "WayBackMachine"
url = "https://web.archive.org/web/20201209123032/http://mateus.great-site.net/?i=1"

[[params.profileMode.buttons]]
name = "Blog"
url = "/posts"


[[params.socialIcons]]
name = "Github"
url = "https://github.com/mateusfg7"

[[params.socialIcons]]
name = "Telegram"
url = "https://t.me/mateusfg7"

[[params.socialIcons]]
name = "Linkedin"
url = "https://linkedin.com/in/mateusfg"


[[params.socialIcons]]
name = "Twitter"
url = "https://twitter.com/mateusfg77"

[params.assets]
disableFingerprinting = true
```
