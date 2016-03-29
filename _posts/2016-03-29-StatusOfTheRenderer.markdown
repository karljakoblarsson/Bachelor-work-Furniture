---
layout: post
title:  "The current state of the OptiX renderer"
author:  Jonatan and Victor
date:   2016-03-29 16:00:00 +0200
categories: renderer
thumbnail: /assets/clothshader/2016-01-26-cbox.png
---


After a lot of reading on OpenGL and OptiX we have finally started with our own project. 
At the time of writing, there are two projects in progress, where both are heavily derived from sample projects. The first project has all the visual effects we are looking for (reflections, textures, etc.), but it can at this point in time only interpret basic geometry, while the second project has no texures or effects, but can read any .obj file that the user specifies. Our current goal is to be able to merge these features: be able to read any .obj file in the first project. 

From our understanding, we will most likely have to design our own custom cuda file for different types of materials as well.

We are also looking at how the camera rotation works and are looking into a better way to move the camera as we are not happy with the current solution, as it can get very disorientating.

