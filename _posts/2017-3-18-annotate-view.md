---
layout: post
title: Annotate view&#58; A simple viewer for semantic segmentation
---

<img src="https://dl.dropboxusercontent.com/s/qqgxyz0tncnccgp/annotate_view.gif" class="teaser-img" />
A simple viewer for semantic segmentation with Qt

**Source:** currently not available...

This application was developed during the work with the fully convolutional networks. It allows to easily traverse the folder with the network's output. It searches for the rgb color images and the corresponding 8-bit grayscale images with semantic information.

Features:


  * Automatically watches specified folder for new image files.
  * Allows to define a color scheme in a simple txt file. Otherwise generates it randomly (with specified random seed).
  * Allows to quickly drag and drop files for viewing.
  * The amount of blending between CCD image and label image can be adjusted.

Example view for the [cityscape dataset](http://cityscapes-dataset.com/).
![annotate_view](https://dl.dropboxusercontent.com/s/qqgxyz0tncnccgp/annotate_view.gif)
