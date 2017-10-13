---
layout: post
title:  "Streaming webcam to HTTP using FFmpeg"
date:   2017-10-12 23:00:00 -0300
categories: streaming
---

`ffmpeg` is an amazing program, you can do lots of crazy things with it.

In this opportunity I will teach you how to stream your webcam to `http` in `mjpeg` format.

In order to accomplish this, we will use the `ffserver` program that comes with `ffmpeg`.

`ffserver` allows us to configure the streaming url, and with `ffmpeg` we will redirect the output of our webcam to there. 

Example `ffserver` configuration file

<script src="https://gist.github.com/llopez/28bc6ee7a1f0650bda5d812b98c79009.js"></script>

Start `ffserver`, use the -f options to specify the configuration file

{% highlight bash %}
  ffserver -f ffserver.conf
{% endhighlight %}

Redirect the webcam output to the `ffserver` feed

MacOS
=====

{% highlight bash %}
  ffmpeg -f avfoundation -i "0" http://localhost:8090/cam.ffm
{% endhighlight %}

Then, you can see your webcam at `http://localhost:8090/cam.mpjpeg`
