---
layout: post
title:  "Developing with Blender"
author:  Jakob
date:   2016-02-22 13:27:34 +0100
thumbnail: /assets/rattan/blender.png
categories: rattan
---

![ Blender interface ]({{ site.baseurl }}/assets/rattan/blender.png)

When developing we start Blender with a template-file and then run
a python-script in it's enviroment which creates the goeometry and sets
material settings among other things.

I created a simple makefile to improve our workflow.
It uses two build targets to either render an image of the geometry, quit
Blender and display it or leave blender open so we can inspect the geometry
manually. The makefile sets a enviroment variable which is then read by the
python script to do different set up.

{% highlight makefile %}
FILE=dev6.blend

OUTFOLDER=out/
OUT=rattan.png

OUTFILE=$(OUTFOLDER)$(OUT)
export OUTFILE

all: export RENDER=1
all:
	blender $(FILE) --background --python test1.py
	open $(OUTFILE)

open: export RENDER=0
open:
	blender $(FILE) --python test1.py

test:
	echo $(OUTFILE)
{% endhighlight %}
