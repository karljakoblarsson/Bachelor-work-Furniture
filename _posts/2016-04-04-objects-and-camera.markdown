---
layout: post
title:  "Importing objects and a cartesian camera"
author:  Jonatan and Victor
date:   2016-03-29 16:00:00 +0200
categories: renderer
thumbnail: /assets/renderer/2016-04-04-rusty-glass.png
---

###Loading object files into the scene

Utilizing the ObjLoader function found in the sutil project, we can easily import objects into our scene, given that it is the only object present in the scene at any given time, so loading a new object will take the old objects place. In order to import several objects at once, we will look closer at the sample project "glass", as it utilizes a similar procedure to import an object into he scene.

![Rendered glass with rusty metal material]({{ site.baseurl }}/assets/renderer/2016-04-04-rusty-glass.png)

As can be seen in the picture above, a glass has been imported into the scene, with the material coming from the tutorial box. An object can be made out of any material; the material simply needs to be defined beforehand.


###Spherical 3D polar coordinates

We are working on transforming the current movement of the camera to instead move according to spherical 3d polar coordinates, as it will make it a lot easier to look around than in the samples. In the samples, it can get quite disorientating, as it is easy to end up sideways or upside down. 
We were able to get the rotation to appear like it worked the way we wanted it after very little work but after trying it a bit more, we encountered a bug making the scene zoom in as we were rotating. After further investigation, we found a lot of small bugs that we have fixed but we haven't been able to fix the bug that zooms in for us. We have decided that we are not going to fix this bug now and have instead added a quite ugly fix that zooms out whenever the rotation causes the program to zoom in. We might go back to this later if we find time for it. Our current guess is that the bug has something to do with out rotation matrix. 
