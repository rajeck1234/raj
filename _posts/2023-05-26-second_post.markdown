---
layout: post
title: "Second Blog Post for GsoC'23"
date:   2023-05-26 02:00:36 +0530
categories: gsoc
tags: kde gsoc
---


## <b> Overview </b>

If you've been following my previous blog posts, you may recall that I've been working on enhancing the user interface of the Bundle Creator in Krita. The new Bundle Creator is to be designed similar to an installation wizard. By compartmentalizing the functionality into four separate sections, users can effortlessly navigate through the various aspects of bundle creation process.

## My Progess so far...

I spent the last two weeks working on the `Resource Chooser` section. The `Resource Chooser` page allows users to users to handpick the resource items they wish to include in their new bundle. The most notable enhancement is the transition from a traditional list view to a more intuitive <b> grid view </b> for the list of available resources, similar to the Resource Manager layout.  

In the previous version, users were required to individually select each resource item and use the `>` key to add them to the list of selected resources. However, now users can simply click on resource items directly to add them to the selected list. This seamless integration of the grid view and the ability to <b> click-to-select </b> greatly streamlines the workflow, especially benefiting tablet users of Krita.

One can also <b> filter resources by tag or name </b> before choosing resource items to be added to the selected list. This allows users to swiftly select resource items that serve a similar purpose when creating a new bundle. Gone are the days of scrolling through the entire list of available items; now, users can easily narrow down their options through efficient filtering.

And finally, to remove a single resource item, users can now simply select it by clicking on it. Similarly, for removing multiple items, users can hold down the Ctrl key and select multiple items imultaneously.Once the desired resource items are selected, users can easily remove them by clicking on the <b> `Remove Resources` button </b>. 

<!-- ![Demp](https://i.postimg.cc/8PRY8wdg/demo4.png) -->
<img src="https://i.postimg.cc/8PRY8wdg/demo4.png" alt="Demo" style="box-shadow: 5px 5px 5px gray;">

### Merge Request 

You can view my merge request [here](https://invent.kde.org/graphics/krita/-/merge_requests/1802).


## Plans ahead

In the upcoming weeks, I would be working on the `Choose Tags` section. This requires some UI related feedback, and if you're interested to help out, please feel free to drop a comment on this [post](https://krita-artists.org/t/bundle-creator-improving-the-ui-ux-design/57405) I created on Krita Artists Forum!

-------------------------------

![My Painting](https://i.postimg.cc/CKWMj6My/Impressionism.jpg)

And just to add a splash of colour to my blogpost, this is just a very quick artwork which I made using Ramon's [impressionism brush bundle](https://www.youtube.com/watch?v=_BuZ4-Gu_Kc&t=922s). It's super easy to use, do check it out! :D