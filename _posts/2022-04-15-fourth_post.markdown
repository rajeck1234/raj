---
layout: post
title: "Digging Deeper into the Math: SoK'22 #4"
date:   2022-04-15 13:03:36 +0530
categories: sok
tags: kde sok
---

## Overview

This is my fourth blogpost for SoK 2022. 

It's been quite some time since my third blogpost. If you remember, I've been working on adding the Perspective Ellipse Assistant Tool in Krita as a part of SoK'22. 

## My Progress so far

### Merge Request and Status Report

Here's the [link](https://invent.kde.org/graphics/krita/-/merge_requests/1343) to my Merge Request.
Also, feel free to check out my [status report](https://community.kde.org/SoK/2022/StatusReport/Srirupa_Datta).


### Creating the Insrcibed Drawable Ellipse

My Perspective Ellipse Assistant Tool looked like this as of March 2022.  

![Animation](/assets/animation2.gif)

But the drawable Ellipse is different from the one shown in the animation. Here drawable Ellipse refers to the ellipse in `krita/plugins/assistants/Assistants/Ellipse.cc`. 


In order to draw the drawable Ellipse, I need to find out the extreme points of the major axis of the ellipse and any other point on that ellipse. Finding out the extreme points of the major axis of the tranaformed ellipse is not a simple task and requires a bit of math, which has been explained in the next section. 



### A bit of math... 

In order to find the extreme points of the major axis of the transformed ellipse, here's what we need to do. 

1. Obtain the equation of the ellipse by solving the tangent equations using the the four points of the four-point-cage, and the touch points of the cage and the ellipse, which in turn can be found by transforming the touch points of the unit square and inscribed circle. 
2. The general equation of an ellipse contains 6 unknowns, namely `(a, b, c, d , e, f)`. Assuming `a` can never be zero, I can divide the equation by `a`, to get 5 unknowns namely `(b/a, c/a, d/a, e/a, f/a)`. 
3. Once I find the 5 coefficients, I can use these to find out the major axis extreme points by the formula shown [here](https://math.stackexchange.com/questions/616645/determining-the-major-minor-axes-of-an-ellipse-from-general-form). 


Here's a [link](https://drive.google.com/file/d/1CtbJcehuN4tO0A9XVX8s2WsOr8J5Kf9-/view?usp=sharing) that demonstrates the above math vividly. Do check it out!

The `KisAlgebra2d::transformEllipse()` helps us to find the major and the minor axis of the transformed ellipse, along with the transformation matrix that we need to apply to the coordinate system. This final transformation is translate + rotate only. However this function works for cases when the circle is centered at the origin. Since our circle is cenetered at `(0.5, 0.5)`, we need to take care of this offest before calling the function. 

Hence the function call should look something like this. 

    QPointF newAxes;
    QTransform newTransform;
    
    QTransform oldTransform = QTransform::fromTranslate(0.5, 0.5) * m_cachedTransform;

    std::tie(newAxes, newTransform) = KisAlgebra2D::transformEllipse(QPointF(0.5, 0.5), oldTransform);


I have not yet understood fully what to do with `newTransform`, and am still talking to my mentors and clarifying some doubts. 
    

## Next Steps

Although the Season of KDE is officially over, I would still be spending a few weeks on this project to complete what's left. I had a great time working and interacting with the devs, and wish to contribute more to open source whenever I get some time off!
