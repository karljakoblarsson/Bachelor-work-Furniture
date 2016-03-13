---
layout: post
title:  "Generating geometry"
author:  Jakob
date:   2016-02-17 10:27:34 +0100
thumbnail: /assets/rattan/first_test.png
categories: rattan
---

We are now able to generate a okay looking object using Blender and it's python
interface.

![A early example of output from our algorithm]({{ site.baseurl }}/assets/rattan/first_test.png)

This prototyp is really simple, the individual strands are identical and just
filped and shifted on the z-axis. We model the strands as NURBS-curves, they
are easy to generate and control. We hope that it will be enough to use
NURBS-curves togehter with bump-maps and other shading technuiqes to render
realistic rattan.

The next step now is to introduce randomness in different ways to make it look
more natural.
