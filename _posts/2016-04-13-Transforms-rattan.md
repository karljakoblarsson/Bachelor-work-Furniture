---
layout: post
title:  "Rattan transforms"
author:  Jakob
date:   2016-04-13 20:03:00 +0100
thumbnail: /assets/rattan/non-linear.png
categories: rattan
---


The latest thing we did was to refactor the code so it generates att geometry in
a [0,1] UV-space and then uses a supplied transform-function to map this
surface into it's final form. The transform-function can be completely
arbitrary. Right now it just takes scaling and position from the selected
object and creates a linear transform using those values.

It takes input as:
![Generated rattan]({{ site.baseurl }}/assets/rattan/transform-before.png)

And produces this output:
![Transformed rattan]({{ site.baseurl }}/assets/rattan/transform-after.png)

But it is possible to create any transform function we would like. The question
now is what to use as input. Choosing the right set of inputs is crucial to
make our tool useful for the artist. If we make the wrong choice our tool will
be useless. We want to provide as much control over the final geometry as
possible but still make it not to tedious. We need the right input to be able
to generate a "good" transform-function. For some value of "good".  Thats one
of the questions, it's not so easy to know what "good" means in this context.

![Example render of a non-linear transfom function]({{ site.baseurl }}/assets/rattan/non-linear.png)

Here is an example render with a non-linear transform-function, in this case
two different quadric functions in the Y and Z-axis.
