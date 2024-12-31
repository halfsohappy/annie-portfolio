---
title: 'Portable Nixie Tube Pomodoro Timer'
subtitle: 'This one has it all: ICs from the 70s! 200 Volts! Extremely Competent Perfboard Circuits! And of course, USB-C.'
date: 2024-9-1 00:00:00
description: 
featured_image: '/images/thumbs/nixie.webp'
permalink: /nixie_pomo/
layout: wider

personal:
class: true
EMB:
DSP:
PCBD:
WOOD:
3D-CAD: true
CS:
---

The main attraction of this one is probably the gorgeous perfboard circuits -- which are my best ever -- so I'll show them off at the top.

<div class="gallery" data-columns="3">
	<img src="/images/nixie/IC1.webp">
	<img src="/images/nixie/IC2.webp">
	<img src="/images/nixie/shift_reg.webp">
	<img src="/images/nixie/power.webp">
	<img src="/images/nixie/to_ribbon.webp">
	<img src="/images/nixie/ribbon_back.webp">
</div>



This page isn't quite done yet -- a full writeup is coming soon!




<h3> Project Summary </h3>

The original idea for this project was a pomodoro timer (a countdown timer that alternates intervals for use as a work/break study technique) that used vintage nixie tubes as a display. I had hoped to exclusively use "retro" parts that were being manufactured in the '70s. 

<h3> Motivation </h3>

I had just taken a digital systems class, and wanted to embark on a project that used my new skills. I had also been to an amzing electronics shop while studying abroad in london (Cricklewood Electronics!) which had thousands of ICs and components that had been collected over many decades, and that inspired the "retro" aspects of this build. My main goals were:

* For the project to only use digital logic. This meant no microcontroller, nothing that could think: Butlerian Jihad rules. <br><br>
* To have a "retro" vibe, I wanted handmade circuits with THT components and DIP packages. I set the (arbitrary) rule that I couldn't use ICs made after the date of my nixie tube decoder ICs, which were mid-70s. This was to avoid having a board that maybe looked "retro" but just had some microcontrollers in DIP packages, or other ICs that made my job "too easy".  <br><br>
* Extremely accurate timekeeping. This was just because I'm a bit of a snob and didn't want to use a 555 timer because it could swing as much as a few minutes if I used the device for a couple hours. <br><br>
* A reasonably compact enclosure so I would actually take it to the library. <br><br>
* The ability to select intervals of work/study, the two most popular being 25/5 and 50/10.

I chose to stretch the '70s rule to not include power components, as I wanted modern high-density Li-Ion batteries and USB-C charging. I also wanted to maximize safety and considering the tubes required 200V, I chose to use a modern boost converter instead of hacking together a flyback.

Ultimately, I ran out of time for this project as the semester got more intense, and so I didn't accomplish all these goals. The clock itself is functional, but just so; I ended up slapping a microcontroller and i2c RTC on it just to have something that worked. It still has 3d printed parts which I don't think fit the retro aesthetic at all, and the enclosure isn't even done being built (it lacks a top plate). There's a lot I'd love to finish, fiz, and optimize on this one when I come back to it!


<h3> Design </h3>

The design was heavily influenced by the size and depth of the nixie tubes, which I mounted in equally retro sockets that were very deep. I wanted to

Put simply, this design was the same as v4.1 but with all components swapped for the smallest componenet of the same type that was still in spec. The LDO went from a classic AMS1117 (SOT-223 package) to the more foreign "NCP706AMX" LDO, which somehow manages >1A of current in a package measuring 1.2 x 1.6mm! Everything that could be 0402 became 0402, and the ESP32C3 module went from the standard WROOM module to the more compact (and more expensive) WROOM-MINI package. The routing was basically "move parts until the nets seem possible, route until you give up, decide to reduce design constraints, repeat" until I got it working.

{% figure %}
<p><img src="/images/abled5pcb/route5.webp" alt="Routing"></p>
{% endfigure %}
	Routing for v5

<h3> Aesthetics </h3>

These are black! Because they are visible on the outside of the bands. The back silkscreen says "She's a runner, She's a Pratt Star", which I put on every one of my PCBs, referencing a Duke joke about the Pratt School Of Engineering.

{% figure %}
<p><img src="/images/abled5pcb/in_hand.webp" alt="Tiny"></p>
{% endfigure %}
	Alright, yea. I got it pretty small.

<!-- This page isn't quite done yet -- a full writeup is coming soon!

![](/images/demo/landscape-01.jpg)

## Demo content

This page is a demo that shows everything you can do inside portfolio and blog posts.

We've included everything you need to create engaging posts about your work, and show off your case studies in a beautiful way.

**Obviously,** we’ve styled up *all the basic* text formatting options [available in markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

You can create lists:

* Simple bulleted lists
* Like this one
* Are cool

And:

1. Numbered lists
2. Like this other one
3. Are great too

You can also add blockquotes, which are shown at a larger width to help break up the layout and draw attention to key parts of your content:

> “Simple can be harder than complex: You have to work hard to get your thinking clean to make it simple. But it’s worth it in the end because once you get there, you can move mountains.”

The theme also supports markdown tables:

| Item                 | Author        | Supports tables? | Price |
|----------------------|---------------|------------------|-------|
| Duet Jekyll Theme    | Jekyll Themes | Yes              | $49   |
| Index Jekyll Theme   | Jekyll Themes | Yes              | $49   |
| Journal Jekyll Theme | Jekyll Themes | Yes              | $49   |

And footnotes[^1], which link to explanations[^2] at the bottom of the page[^3].

[^1]: Beautiful modern, minimal theme design.
[^2]: Powerful features to show off your work.
[^3]: Maintained and supported by the theme developer.

You can throw in some horizontal rules too:

---

### Image galleries

Here's a really neat custom feature we added – galleries:

<div class="gallery" data-columns="3">
	<img src="/images/demo/square-01.jpg">
	<img src="/images/demo/portrait-02.jpg">
	<img src="/images/demo/square-02.jpg">
	<img src="/images/demo/square-03.jpg">
	<img src="/images/demo/square-04.jpg">
	<img src="/images/demo/landscape-05.jpg">
</div>

Inspired by the Galleries feature from WordPress, we've made it easy to create grid layouts for your images. Just use a bit of simple HTML in your post to create a masonry grid image layout:

```html
<div class="gallery" data-columns="3">
    <img src="/images/demo/square-01.jpg">
    <img src="/images/demo/portrait-02.jpg">
    <img src="/images/demo/square-02.jpg">
    <img src="/images/demo/square-03.jpg">
    <img src="/images/demo/square-04.jpg">
    <img src="/images/demo/landscape-05.jpg">
</div>
```

*See what we did there? Code and syntax highlighting is built-in too!*

Change the number inside the 'columns' setting to create different types of gallery for all kinds of purposes. You can even click on each image to seamlessly enlarge it on the page.

---

### Image carousels

Here's another gallery with only one column, which creates a carousel slide-show instead.

A nice little feature: the carousel only advances when it is in view, so your visitors won't scroll down to find it half way through your images.

<div class="gallery" data-columns="1">
	<img src="/images/demo/landscape-02.jpg">
	<img src="/images/demo/landscape-03.jpg">
	<img src="/images/demo/landscape-04.jpg">
</div>

### What about videos?

Videos are an awesome way to show off your work in a more engaging and personal way, and we’ve made sure they work great on our themes. Just paste an embed code from YouTube or Vimeo, and the theme makes sure it displays perfectly:

<iframe src="https://player.vimeo.com/video/107469489" width="640" height="360" frameborder="0" allowfullscreen></iframe>

---

## Pretty cool, huh?

We've packed this theme with powerful features to show off your work.

Why not put them to use on your new portfolio?

<a href="https://jekyllthemes.io/theme/board-portfolio-jekyll-theme" class="button button--large">Get This Theme</a> -->