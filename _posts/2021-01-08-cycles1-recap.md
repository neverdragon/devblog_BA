---
layout: post
title: Understanding Cycles - recap, because I waited way too long to create this blog
---

We've been trying to understand the Blender/Cycles rendering source coude for a while now.
Here is a very short recap:

* tried to understand/work with the connection between Blender and Cycles to be able to determine what changed in the scene between frames
* abandoned this approach as we figured out that we should have all necessary information within Cycles already
* focused on understanding Cycles code, with is in C++ and more familiar to me than the C code that makes up Blender

Currently I'm focussing on understanding the render transformation in Cycles to be able to calculate pixel-space bounding boxes for objects that we can then use to determine with areas to render, and (for now) setting the render region border accordingly.

So far I have found that the Cycles camera class has the following potentially relevant matrices saved:
  ProjectionTransform worldtoraster;
  ProjectionTransform worldtoscreen;
  ProjectionTransform worldtondc;
  Transform worldtocamera;
  
