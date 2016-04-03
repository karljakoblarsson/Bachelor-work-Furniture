---
layout: post
title:  "Woven cloth general API"
author:  Vidar
date:   2016-04-02 02:03:00 +0100
thumbnail: /assets/clothshader/2016-04-02-api.png
categories: clothshader
---

One of the goals of the cloth shader project was to develop a shader for V-Ray, the commercial renderer used at IKEA.
While all of our initial work had been done using Mitsuba, before our visit to ICOM some weeks ago we wanted to take a first shot at a V-Ray implementation.
We did this by simply copying all the code and adapting it to work with the V-Ray API. While this may seem like a very primitive approach, it allowed us to
easily see the changes needed.

When this was done, and the shader worked within V-Ray, I begun unifying the code by identifying common functions between the two shaders and creating a general API for our model.
This should hopefully make porting the shader to further rendering engines much easier.

## Initializing the model

All parameters to the model are entered into the struct `wcWeaveParameters`,
{% highlight c++ %}
typedef struct
{
// These are the parameters to the model
    float uscale;
    float vscale;
    float umax;
    float psi;
    float alpha;
    float beta;
    float delta_x;
    float intensity_fineness;

// These are set by calling one of the wcWeavePatternFrom* functions
// after all parameters above have been defined
    uint32_t pattern_height;
    uint32_t pattern_width;
    PaletteEntry * pattern_entry;
    float specular_normalization;
} wcWeaveParameters;
{% endhighlight %}

After this is done, one of the functions `wcWeavePatternFromWIF` or `wcWeavePatternFromData` needs to be called. This is what defines the pattern of the cloth, either by reading a WIF file, or by using data defined by the user.
{% highlight c++ %}
void wcWeavePatternFromWIF(wcWeaveParameters *params, const char *filename);
void wcWeavePatternFromData(wcWeaveParameters *params, uint8_t *pattern,
    float *warp_color, float *weft_color, uint32_t pattern_width,
    uint32_t pattern_height);
{% endhighlight %}
This is all that needs to be done before the rendering begins.

## Shading

During rendering, two functions are of intersest.
The first one,
{% highlight c++ %}
wcPatternData wcGetPatternData(wcIntersectionData intersection_data,
    const wcWeaveParameters *params);
{% endhighlight %}
returns a struct `wcPatternData` containing all important information about the weave at
the shaded point, such as color, normal and whether the warp or the weaft is on top at this point.
This function expects an instance of `wcIntersectionData`, which needs to be filled in with
information of the intersection aquired from the renderer.
{% highlight c++ %}
typedef struct
{
    float uv_x, uv_y;
    float wi_x, wi_y, wi_z;
    float wo_x, wo_y, wo_z;
} wcIntersectionData;
{% endhighlight %}

Finally, the function
{% highlight c++ %}
float wcEvalSpecular(wcIntersectionData intersection_data,
    wcPatternData data, const wcWeaveParameters *params);
{% endhighlight %}
evaluates the model and returns the amount of specular reflection at this point.

