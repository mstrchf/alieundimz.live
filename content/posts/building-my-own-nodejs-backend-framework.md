---
title: Building my own Node.js backend framework 📖
date: 2022-03-26T09:00:00Z
tags:
    - notexpress
categories:
    - general programming
keywords:
---

Since I started using Node.js until few months ago, I have not really delved deep into the nitty-gritty.

Whenever I work on a backend project, I tend to use Express.js all the time with its rich middleware eco-system. This is not bad at all, but I realized that, I couldn’t really get serious work done with the knowledge I have on Node.js. I felt like too much abstractions like Express.js were limiting me in some sort of way. As a result, I took it upon myself to create my own backend framework without any external dependencies to reduce the abstractions on top of Node.js. This was meant to be solely for educational purposes.

Since I have been using Express.js as my backend framework for some time, I decided to base by framework on it. My implementation is to be done in such a way that it is almost indistinguishable from Express.js. Having implemented almost all of its features, I plan to add into it features that weren’t available in Express itself.

During the initial project phase, having implement a few features, I noticed that there are quite a few projects out there that are based on Express. This kind of made me feel some sort of way because my project might be thought of as just another clone. It didn’t stop me though because my main reason is to test and improve my Node.js knowledge . If I end up having something that other people might want to use, it’s just added bonus.

## Overview of notexpress in action
You can see the resemblance of the syntax with Express.js
```Javascript
const notexpress = require("@ndimz/notexpress");
const app = new notexpress();

app.get("/", function (req, res) {
  res.send("Goodday World");
});

app.listen(5000);
```
## Why am I building yet another?
As briefly mentioned earlier, the main motivation for me to build “yet another framework“ is to learn.

I figured out that there is a lot of stuff that I simply brushed upon while I was getting started with Node.js. I could remember the first tutorials and blog posts are watched and read, jumped to Express within a few minutes. This worked for me for some time. But as I moved on, I found out that there is a lot more that can be done with just Node.js alone. Until recently did I find out about _Node.js Addons_. You could run entire compiled C++ code right in Node.
## The way forward
There is not much I can say about the future of the project.

One thing I am certain is the fact that, I will make sure to have every single feature implemented. That is guaranteed. Additional features are something I really want to include but I cannot really promise that they will happen because this is much like an experiment for me. Once my objectives are met, it solely depend on availability and may be on how much love it receives.
## Conclusion
This framework is by no means intended for large scale
  production use. It is a mere proof-of-concept. So please, be
  cautioned. Project is hosted [on GitHub](https://github.com/ndimzKM/notexpress) and [npm](https://www.npmjs.com/package/@ndimz/notexpress).
