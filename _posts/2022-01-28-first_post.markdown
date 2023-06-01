---
layout: post
title: "First Blog Post for SoK 2022!"
date:   2022-02-01 13:03:36 +0530
categories: sok
tags: kde sok
---
![My Painting](https://i.postimg.cc/PqdgrknP/starry-night2.png)

## About Me 

I’m Srirupa Datta, a third year undergraduate studying Electrical Engineering at Jadavpur University, India. This year, I have decided to take part in Season of KDE and will be working on extending the Ellipse Assistant Tool to add support for Perspective Ellipse in Krita.

## My Introduction to Qt and Krita

As a painter who also likes software development, I first came across Krita when I was looking for digital painting applications on Windows. Later on, I learned about open source and decided to start contributing as a way to build my development skills while working on something that I myself use. I spent the last few months of 2020 building Krita, first in Windows (a nightmare :P), then in Linux, and started learning Qt since I was already familiar with some basic C++ from school.

Since then, I have fixed some minor bugs in my free time, including [Warn when exporting layers with multiple transparency masks into .psd](https://invent.kde.org/graphics/krita/-/merge_requests/801) and [Convert Colorize Mask to Paint Layer before splitting layers](https://invent.kde.org/graphics/krita/-/merge_requests/894). After becoming somewhat familiar with Krita’s huge codebase, I started looking for something more challenging to implement and came across this [Feature request: Circle in a Square Assistant Tool](https://bugs.kde.org/show_bug.cgi?id=405643) .

Once I learnt about Season of KDE, I decided to apply for it and cooked up a [proposal](https://season.kde.org/project/88) to implement this feature request and Halla was kind enough to agree to mentor me!

## Project Details

#### Overview
This project aims to create a tool that is essentially an adjustable four corner mesh that always has an ellipse inside it which touches the sides, in order to draw ellipses in perspective with ease.
The attachment below, provided by Hector demonstrates how the tool is supposed to work:

![circle in square tool](https://bugsfiles.kde.org/attachment.cgi?id=122943)

#### Benefit
Developing this tool would make it easier to draw ellipses in perspective. Currently, to draw a circle in a square with the ellipse tool, one needs to draw the diagonals of the square and correctly align the axis of the ellipse to the square, which is rather complicated since it takes time to set a concentric ellipse with the current ellipse tool. With the circle in a square tool, one just needs to set the four corners of the square.
Hector, who created this feature request is also willing to test this feature while it's being developed!
