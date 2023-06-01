---
layout: post
title: "Inscribing the Ellipse: SoK'22 #3"
date:   2022-03-06 13:03:36 +0530
categories: sok
tags: kde sok
---

## Overview

This is my third blogpost for SoK 2022. 

If you have been following my [earlier](https://srirupa19.github.io/sok/2022/02/01/first_post.html) [blogposts](https://srirupa19.github.io/sok/2022/02/13/second_post.html), you would know that I've been working on adding the Perspective Ellipse Assistant Tool in Krita. 

## My Progress so far

#### Created a Merge Request

Here's the [link](https://invent.kde.org/graphics/krita/-/merge_requests/1343) to my Merge Request, you can check if you want to!


#### Creating the Insrcibed Ellipse

Two weeks back this is what my tool looked like. 

![Tool1](/assets/prev.png)

Then I spent almost a week scratching my head over the mathematics required to transform a circle inscribed inside a unit square to an ellipse inscribed inside my quadrilateral. Dmitry suggested a nice [tutorial](https://www.scratchapixel.com/lessons/3d-basic-rendering/perspective-and-orthographic-projection-matrix/building-basic-perspective-projection-matrix) on projection matrices and geomtery. Going through a few lessons made all the mathematical code less intimidating. 


Since I already had a four cornered assistant, all I needed to do was to add it's inscribed ellipse. 

This is roughly what's done:
- The transformation matrix is set for the canvas.
- A unit square is added to path, which on being drawn on the canvas gets converted to the transformed quadrilateral.
- The inscribed circle for the unit square, as expected, gets converted to the inscribed ellipse for our quadrilateral.  

#### A bit of code... 

Here's a little bit of code demonstrating the above procedure. Anyone not familiar with Krita's codebase can skip directly to the animation!

First, inside the `PerspectiveEllipseAssistant::drawAssistant()`, the transformation matrix of the canvas is set using:

    gc.setTransform(converter->documentToWidgetTransform());

Now, the following code draws a valid four cornered assistant. 

    QPainterPath path;
            for (int y = 0; y <= 1; ++y)
            {
                QLineF line = QLineF(QPointF(0.0, y), QPointF(1.0, y));
                KisAlgebra2D::cropLineToRect(line, gc.window(), false, false);
                path.moveTo(line.p1());
                path.lineTo(line.p2());
            }
            for (int x = 0; x <= 1; ++x)
            {
                QLineF line = QLineF(QPointF(x, 0.0), QPointF(x, 1.0));
                KisAlgebra2D::cropLineToRect(line, gc.window(), false, false);
                path.moveTo(line.p1());
                path.lineTo(line.p2());
            }

And finally, once I draw the circle inside the unit square, I have my Perspective Ellipse! All I had to do was to add this piece of code:

    path.addEllipse(QPointF(0.5, 0.5), 0.5, 0.5); 

And here's a small animation demonstrating the current Perspective Ellipse Assistant Tool!

![Animation](/assets/animation2.gif)

## Next Steps

I would spend the next few weeks working on drawing and snapping related code. That should hopefully complete my assistant!

