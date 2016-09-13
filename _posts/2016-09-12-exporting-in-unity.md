---
layout: post
title:  "Exporting Assets in Unity 5"
date:   2016-09-12 01:43:15 -0700
categories: ["Unity"]
---

Exporting assets in Unity 5 isn't as easy as it seems.

The default behavior when exporting assets is to export the selected asset, and all available scripts.
if you have dependencies between scripts / objects in your scene, Unity will export all available scripts.

This is a debatable solution, but it was not what I wanted.
I was looking to export a single prefab which had a single dependent script.

Step 1:
  Right click the asset you're exporting, then select "Select Dependencies" from the contextual menu.
  This should select all dependencies between that asset and your scene.

Step 2:
  With the asset and dependencies selected, right click and select "Export Package".
  This will open a small 'export' window listing all items which will be exported.
  Initially, it will show the prefab you want to export and ALL AVAILABLE scripts.

Step 3:
  Untick the 'Include dependencies' box at the bottom of the export window.
  This will reduce the selection to only the items you have selected in your scene (the asset and all of it's dependencies).

Step 4:
  Click the 'Export' button in the lower right-hand corner.

Congratulations! :tada: you've exported you're asset and all of it's wonderous dependencies.

One caveat: Unity doesn't detect inheritence heirarchies when identifying dependencies between scripts.
So if you have a 'child' script, which inherits from a 'parent' script and is present on an object, Unity won't detect the 'parent' as a dependency, even though your object won't export correctly.
