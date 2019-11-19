---
layout: post
title:  "Create blog on github.io"
date:   2019-11-19 17:00:00 +0900
categories: jekyll update
---

```sh
$ sudo gem install jekyll
$ mkdir ~/blog && cd ~/blog
$ jekyll new twinbie.github.io
$ jekyll serve
$ curl http://localhost:4000 #test
```

Create the repository "twinbie.github.io"

```sh
$ cd ~/blog/twinbie.github.io
$ echo "# twinbie.github.io" >> README.md
$ git init
$ git add *
$ git commit -m "first commit"
$ git remote add origin https://github.com/twinbie/twinbie.github.io.git
$ git push -u origin master
```

