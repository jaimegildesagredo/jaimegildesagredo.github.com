---
layout: post
title: A python RESTful API consumer
author: jaimegil
tags: development, finch, python
---

[Web APIs][webapis], and more particularly [RESTful][restful] APIs, have become very popular in the last few years by the hand of large sites like Fakebook, Twitter or Github, who give developers the opportunity to extend their services with a wide variety of applications and services.

This huge growth in the development and use of REST APIs has been mainly because of the ease of consuming data from different services to create applications, tools or whatever you imagine, such as another APIs! on nearly any device, operating system or programming language. And what has made this possible? The answer is the [HTTP protocol][http].

## Consuming REST APIs

Right, let me show you how easy is to start playing with, for example, the [Github API][github_api], using Python and the awesome [Requests][requests] http library.

<script src="https://gist.github.com/4356685.js">
</script>

It's so easy! We only have needed to make a GET request to the user repositories endpoint and wait for an OK response to display a list of repository names and programming languages.

We also could add a new repository to the list making an authenticated POST request to the repositories endpoint and including some data.

<script src="https://gist.github.com/4356841.js">
</script>

These two previous examples shown very simple use cases, but serve to show the simplicity of consuming REST APIs.

But unfortunately, in the real world, client applications tend to become more and more complex and begins to be necessary to write some boilerplate code for stuff like prepare requests, validate data and parse responses.

[webapis]: http://en.wikipedia.org/wiki/Application_programming_interface#Web_APIs
[restful]: http://en.wikipedia.org/wiki/Representational_state_transfer
[http]: http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
[requests]: http://python-requests.org
[github_api]: http://developer.github.com/v3/repos/
