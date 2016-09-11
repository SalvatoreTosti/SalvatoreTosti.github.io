---
layout: post
title:  "Isometric Lighting in Unity 5+"
date:   2016-08-07 19:43:15 -0700
categories: ["Unity"]
---

A quick fix for a strange problem.  
I recently ran into a strange lighting behavior in Unity 5.3.3.  
Some objects in my scene appeared to be lit more strongly as they approached the edge of the camera's view.

![lighting before](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_before.png)

The camera was orthographic and the materials on the objects were very simple _(just a base color and highlight color)._ Adjusting the light's configuration and fiddling with the global lighting settings seemed to yield no discernible results.

After some research, I found [a related stack exchange question](http://gamedev.stackexchange.com/questions/122104/unwanted-highlight-on-far-side-of-objects-near-the-edges-of-the-screen-when-usin).  
The answer explains that Unity 5+'s standard shader uses Fresnel reflection and can produce unexpected lighting behavior when using orthographic cameras.  

Following that answer's suggestion, I changed the material to use a Legacy / Diffuse shader.

![select legacy lighting](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_lighting_select_legacy.png)

This changed the specularity of the material and resolved the issue.

![lighting after](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_after.png)

Because the material changed how light was reflected, it also changed the 'normal' behavior of the material.  
Here's an image which shows the change in specularity on a house which was not affected by the large specularity jump.

![lighting comparison](/assets/post_images/2016-08-07-lighting-materials-in-unity/house_comparison.gif)
