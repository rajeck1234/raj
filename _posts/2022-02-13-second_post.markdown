---
layout: post
title: "Second Blog Post for SoK 2022"
date:   2022-02-13 13:03:36 +0530
categories: sok
tags: kde sok
---

## Perspective Ellipse Assistant in Krita 

Hello, this is my second blogpost for SoK 2022. 

In my previous blogpost, I wrote that I'll be working on extending the Ellipse Assistant Tool to add support for Perspective Ellipse in Krita. However, last week my mentors and I decided that as of now, it makes more sense to add a new Assistant Tool for Perspective Ellipse instead of extending the Ellipse Assistant Tool. 

## My Progress so far

### Adding a new Assistant Tool

Here's the Tools Option Docker after the new Perspective Ellipse Assistant is selected!

![Tools Option Docker](/assets/toolbox.png)

### Creating an adjustable Four Cornered Convex Quadrilateral

Anyone familiar with Assistant Tools in Krita would have noticed that the current Perspective Assistant Tool draws an adjustable convex quadrilateral with grid lines. I decided to take advantage of that and reused the existing code, got rid off the grid lines, and voila! I've a four cornered mesh for my Perspective Ellipse Assistant.

![Difference](/assets/difference.png)

For people who are familiar with Krita's codebase:

I added `PerspectiveEllipseAssistant.h` and `PerspectiveEllipseAssistant.cc` to the `ktita/plugins/assistants/Assistants` directory which currently contanis files for all the other assistant tools in the form XAssistant.h/cc, where X is the Assistant name. 
Then, I registered my Assistant by including the following piece of code in the assistant_tool.cc file. 

    KisPaintingAssistantFactoryRegistry::instance()->add(new PerspectiveEllipseAssistantFactory);

And there, my four cornered mesh works exactly how it's expected too! ;)

![Animation](/assets/animation.gif)

## Next Steps

I would spend the next few weeks creating an inscribed ellipse inside my four cornered mesh. This, however, is going to take some time as I am not yet fully comfortable with the mathematics involved. 

For this part, I want to transform a circle to an ellipse using a transformation matrix, given that the equation for the circle and the transformation matrix is given. I'm looking for a way to obtain the coefficients of the equation for the corresponding transformed ellipse.

Anyone having any leads on this can feel free to mail me [here](kumarutkarsh946@gmail.com). Thanks in advance!
