---
layout: post
title:  "Brushing up on graphics"
author:  Jonatan and Victor
date:   2016-02-29 16:00:00 +0200
categories: renderer
thumbnail: /assets/renderer/2016-04-04-rusty-glass.png
---

###OpenGL Tutorials

Our end goal is to build a renderer. To get a start on our project, we decided to run through the tutorials by Ulf Assarsson designed for the Computer Graphics course at Chalmers. The aim of this was to give us an understanding of the basics of computer graphics and primarily OpenGL. Our plan is for the final renderer to implement both rasterization (using OpenGL) and ray-tracing (using OptiX), so learning rasterization is a very good starting point. Also, the final assignment in the course is designing a path tracer (a type of ray-tracer) using OpenGL. While the goal is to build our ray-tracer in optix and not in OpenGL (the OpenGL solution will be incredibly slow), designing a path tracer using OpenGL is a solid foundation to understand the structure of ray-tracing.


*Insert picture of lab 5 or 6 here


The picture portrayed above displays what the final rasterization renderer looks like. It applies lighting effects using the blinn-phong model, where factors such as ambient, diffuse and specular lighting is considered in order to generate images as visually correct as possible under the limitations of rasterization.
