---
layout: post
title:  "Isometric Lighting and Materials in Unity"
date:   2016-05-02 19:43:15 -0700
categories: unity
---

I recently ran into a lighting problem in Unity which seems relatively undocumented.  
Some objects in my scene appeared to be lit more strongly as they approached the edge of the camera's view.

![lighting before](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_before.png)

The camera was orthographic and the materials on the objects were very simple (just a base color and reflection color).  
Initially I assumed this was a lighting issue, specifically I thought the light was not producing parallel rays, but angled rays which diverged from a single point, like a spotlight.  
However, adjusting the light's settings and fiddling with the global lighting settings seemed to yield no discernible results.


After some research, I found [a related stack exchange question](http://gamedev.stackexchange.com/questions/122104/unwanted-highlight-on-far-side-of-objects-near-the-edges-of-the-screen-when-usin).  
The answer explains that Unity 5+'s standard shader uses Fresnel reflection and can produce unexpected lighting behavior when using orthographic cameras.  
Following the answer's suggestion, I changed the material to use a Legacy / Diffuse shader.

![select legacy lighting](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_lighting_select_legacy.png)

This changed the specularity of the material and resolved the issue.

![lighting after](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_after.png)

Because the material changed how light was reflected, it also changed the 'normal' behavior of the material.
Here's an image which shows the change in specularity on a house which was not effected by the large specularity jump initially.

![lighting comparison](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_comparison.gif)
