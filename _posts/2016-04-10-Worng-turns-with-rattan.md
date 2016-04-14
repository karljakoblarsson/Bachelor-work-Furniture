---
layout: post
title:  "Wrong Turns with Rattan"
author:  Jakob
date:   2016-04-10 20:03:00 +0100
thumbnail: /assets/rattan/turns.png
categories: clothshader
---

![Example of or geometry]({{ site.baseurl }}/assets/rattan/turns.png)

A few weeks ago we finished one variation of the pattern where the rattan
attaches to the frame, or "turn". The results can be seen above. As a result of
this the geometry now consists of one long spline instead of one for each row.
This is good since rattan strands can be several meters long (Unfortunately
I don't have a good source for this) but now we need to figure out when to end
one strand, create a transition and start the next. This is something we hope
to address later in the project.

After that milestone we wanted to continue by trying to create the transition
between two different weaving patterns. We didn't know were to start and since
we hadn't found and previous work in this area we were stuck.

After a tip from Marco, our supervisor, we started to look into frame fields, as described in this paper: [Frame Fields: Anisotropic and Non-Orthogonal Cross Fields](http://cs.nyu.edu/~panozzo/papers/frame-fields-2014.pdf). The paper which was published
last year utilizes so called frame fields to improve re-meshing to make sure
a mesh behaves well during animation. The thought was that our problem is
similar to the problem of re-meshing, call it "re-weaving" if you will.

It was quite challenging to get into since we don't have so much knowledge of
the domain. Frame fields is a generalization of Cross fields but we probably
don't need the extra properties provided by frame fields. But unfortunately
cross fields doesn't seem to help us with the "re-weaving" problem.

Since that didn't lead anywhere we were really stuck. This happened at the
same time as the exam-period, easter break and re-exam-period so because of
that we didn't do any progress for several weeks.

After consultation with the rest of the group we now changed our focus to
another problem, the modeling interface and the input to our algorithm, and we
are progressing again.
