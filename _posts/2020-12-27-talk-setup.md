---
layout: post
title: Academic talk setup - slides and virtual board
date:   2020-12-27
description: Giving a talk with slides and a tablet (by Zoom).
---

Last Monday, I had the pleasure of presenting our work with Benjamin Guedj, María Pérez-Ortiz, and John Shawe-Taylor, [*A PAC-Bayesian Perspective on ILE Structured Prediction*](https://arxiv.org/abs/2012.03780) to the Benjamin's group at UCL. It was great to get impressions on the work from the other students and postdocs in the group.

Inspired by many researchers who have been honing the craft of Zoom presentations{% fn %}, I spent a bit of time perfecting a setup that would allow me to give the talk using slides that I could annotate throughout the talk. I found that this would be closer to what the talk would have looked like, had we been all in a conference room in London.

The goal of the setup is to **annotate PDF presentations while presenting** using a graphical tablet. I had a beamer prepared but intended to add illustrations and diagrams during the presentation. It proved very useful when I was asked questions!

For future reference, this post documents the setup.

### Ingredients: hardware & software

#### Hardware:

* **Laptop:** you'll need access to a keyboard for to navigate efficiently during the presentation.
* **Wacom tablet:** One by Wacom Medium (60 euros). I chose a Wacom (over a cheaper knock-off) because I had found the Ubuntu drivers ahead of time!

#### Software 
The software linked here is on Ubuntu 18.04, but everything should work on other platforms.

* Wacom drivers{% fn %}
* `Zoom` for the meeting
* `Xournal++` for presenting and annotating.

### In a nutshell

At a high-level the setup is as follows:

* `Xournal++` in `Presentation mode`.
* `Zoom`, sharing the *portion of the screen* that corresponds to the slides in `Xournal++`.

During the presentation, I used `Xournal++` keyboard shortcuts to avoid switching between the mouse and the stylus (see below).

In this rest of this article, I'll focus on setting up `Xournal++` for presenting and annotating.

### Xournal++: introduction

From the [`Xournal++` website](https://xournalpp.github.io/):

> `Xournal++` is an cross-platform, open source, hand note-taking software with the target of flexibility, functionality, and speed. 

It has a rich set of features -- in particular it can be extended through `Lua` plugins -- but I only used the most basic ones. Note: the `Xournal++` User Guide is currently WIP but the [User Manual](https://github.com/xournalpp/xournalpp/wiki/User-Manual) in Github is quite complete.

`Xournal++` worked out of the box. During the presentation I used the out-of-the-box configuration of `Xournal++` in *Presentation Mode*. My window looked like this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/talk-post-xournalpp.png">
    </div>
</div>
<div class="caption">
Xournal++ window with default configuration, in Presentation mode.
</div>

Then, I simply shared a portion of my screen in Zoom to crop out the toolbars.

### Navigation during the presentation: keyboard shortcuts
The three essential keyboard shortcuts in Xournal++:
* Go to previous/next slide: <kbd> Ctrl </kbd> + <kbd> PageUp</kbd>/<kbd> PageDown </kbd>
* Switch to the `Eraser` tool: <kbd> Shift </kbd> + <kbd> Ctrl </kbd> + <kbd> E </kbd> 
* Switch to the `Pen` tool: <kbd> Shift </kbd> + <kbd> Ctrl </kbd> + <kbd> P </kbd>

**Note:** when going back and forth between slides, the position of the slide can sometimes change slightly. I need to look into this, but it was not problematics for the talk because the change was small enough.

### Xournal++: going further

While writing down this setup for future reference, I realized that there was low-hanging fruit in making my setup better.

Here are some of the problems I encountered using the talk... Note that these are all linked to default behavior in Xournal++ and do not represent actual limitations of the software. We'll see that they can all be easily fixed.

#### Multiple monitors
I had initially planned on using my external monitor for the presentation and my laptop screen for seeing faces. However, the tablet was mapped to the union of both monitors which made drawing difficult. Here's an example of how that impacted my ability to annotate:
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/talk-post-multiple-monitors.png">
    </div>
</div>
<div class="caption">
On the left, in the red circle, when both monitors were used. On the right, in the orange circle, when only one was used.
</div>

This fix was a bit hacky... what if I had really needed the second monitor, e.g. for notes? 

In retrospect, I should have remapped the tablet to a **single monitor**, and used **relative tracking**. In `System Settings > Wacom Tablet`
<div class="row">
    <div class="col-12">
        <img class="mx-auto d-block img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/talk-post-mapping.png">
    </div>
</div>
<div class="caption">
Mapping to a single monitor in Ubuntu `System Settings > Wacom Tablet`.
</div>

#### Default eraser behavior
By default, the eraser is in `whiteout` mode. It removes any content where it is applied and replaces with white pixels. This is true for both the PDF content (i.e. the slides) and any pen strokes I addded. Two consequences: I would remove content from the slides (which isn't the goal in general) and the resulting white pixels would be more white that the off-white background my PDF had...

The fix is very simple: **change eraser behavior from `whiteout` to `delete stroke`**.

> **Note:** settings are saved from one session to the next so you shouldn't have to reset this every time.

#### Adding pages
At one point I ran out of space on a slide. To continue the explanation, an easy solution is to add a page. However, to be able to export the PDF of the annotations afterwards, it is best to keep all the pages the same size.

To configure adding a new page there are two steps:
1. Choose the paper type: `Xournal++` offers many options.
2. Configure the paper size: choose to keep the current size which will adapt to your presentation.

Note that it may be necessary to duplicate a slide, for example to answer two separate questions concerning the same slide. This requires chaning the default background which a bit long to do during the presentation. It is best to go to a new blank slide instead.


## Wrap-up

`Xournal++` works perfectly for my (rather simple) needs. If you know of alternatives, don't hesitate to let me know!

<code>Xournal++</code> is a very active project and is looking to be more widely known. Check out their <a href="https://github.com/xournalpp/xournalpp/issues/2045">Github issues</a> if you'd like to help whether in the code or in documentation and outreach.

-------------------------------------------------------------------------

{% footnotes %}
   {% fnbody %}
      Especially my Professors at Sorbonne Unversité, and all those who have been giving pandemic seminars online! Another source of inspiration is <a href="https://freakonometrics.github.io/videos/">Arthur Carpentier</a>, who has been posting lectures online.
   {% endfnbody %}
   {% fnbody %}
I won't be getting into how to install these here.
   {% endfnbody %}
{% endfootnotes %}
