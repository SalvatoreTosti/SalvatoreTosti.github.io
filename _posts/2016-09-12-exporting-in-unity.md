---
layout: post
title:  "Exporting Assets in Unity 5"
date:   2016-09-12 01:43:15 -0700
categories: ["Unity"]
---

Exporting assets in Unity 5 isn't as easy as it seems.

The default behavior when exporting assets is to export the selected asset, and __all available__ scripts. This is a debatable solution, but it was not the behavior I desired.
I wanted to export a single prefab which had a single dependent script.  

To achieve this, I used the following technique:

__Step 1:__
  Start by locating the assets you want to export.
  My example is a prefab with one script attached.

  ![script on prefab](/assets/post_images/2016-09-12-exporting-in-unity/script-on-prefab.png)


  ![prefab](/assets/post_images/2016-09-12-exporting-in-unity/prefab.png)

__Step 2:__
  Right-click the asset you're exporting, then click _Select Dependencies_ from the contextual menu.

![select dependencies](/assets/post_images/2016-09-12-exporting-in-unity/select-dependencies.png)

  This should select all dependencies for the asset.

![after select dependencies](/assets/post_images/2016-09-12-exporting-in-unity/after-select-dependencies.png)


__Step 3:__
  Select the asset and all of its dependencies, then right-click and select _Export Package_.

![export package](/assets/post_images/2016-09-12-exporting-in-unity/export-package.png)

  This will open a small "export" window listing all items which will be exported.
  Initially, it will show the asset you're are exporting as well as __All Available__ scripts.

![after export package](/assets/post_images/2016-09-12-exporting-in-unity/after-export-package.png)  

__Step 4:__
  Untick the _Include dependencies_ box at the bottom of the export window.
  This will reduce the selection to only the items you have selected in your scene (the original asset and all of its dependencies).

![after box untick](/assets/post_images/2016-09-12-exporting-in-unity/after-box-untick.png)  

__Step 5:__
  Click the _Export_ button in the lower right-hand corner and select where the package should be saved.

Congratulations! :tada: you've exported your asset and all of its wondrous dependencies.

__One caveat:__ Unity doesn't detect inheritance hierarchies when identifying dependencies between scripts.
If you have a _child_ script which inherits from a _parent_, Unity won't detect the _parent_ as a dependency, and your exported _child_ script will not compile.
