---
layout: post
title:  "Anti-aliasing and Multiple rays"
author:  Vidar
date:   2016-04-23 02:03:00 +0100
thumbnail: /assets/renderer/2016-05-05-pre-anti-aliasing.png
categories: renderer
---

%%%Anti-aliasing
Ever since the cloth material was integrated with OptiX, I noticed that there were "creases" in the cloth material that shouldn't be there which looked like pixelated ripples. It was apparent that this was due to aliasing and it bothered me to such an extent that I decided to fix it.

By applying a jitter to the ray tracing, the ray randomly samples with a slight offset in a randomized direction, by a jitter-factor's distance. While this makes the picture ever so slightly blurry, it removes many visual bugs like the pixel ripples.

![Pre-anti-aliasing]({{ site.baseurl }}/assets/renderer/2016-05-05-pre-anti-aliasing.PNG)

%%%Multiple rays per pixel
By utilizing the new anti-aliasing function, the camera can now shoot several rays in randomized directions on a sub-pixel level. Before this, shooting multiple rays would have no effect, as each pixels' ray would be identical no matter how many rays you shot. Now, shooting several rays per pixel with a slight randomized offset, one can set an average colour over all of the samples of a pixel, rendering a much more realistic image.

Worth noting is that the amount of shadow rays shot out per pixel will now multiply by how many light samples per pixel are done.