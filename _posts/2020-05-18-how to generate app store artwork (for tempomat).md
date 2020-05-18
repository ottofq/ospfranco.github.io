---
layout: post
title: How to create assets for your App (Artwork, Icons, etc)
excerpt: A guide for the solo developer to leave designers out of work
date: 2020-05-18 09:00:00 -04:00
categories: post
permalink: /:categories/:year/:month/:day/:title/
location: Munich
image: assets/taco.png
twitter:
  username: "ospfranco"
  card: "summary_large_image"
  image: "assets/taco.png"
---

So I recently had a small twitter exchange with Jamie Birch, he wanted to generate some artwork for Lingua Franca, I shortly explained my workflow, and I think it is a interesting topic to explore further, so I'm just going to line-out how I do it, it is by no means the perfect way, it might not be even a good way, but if anyone finds it useful or can show me a better way, then would be more than happy.

So, [Tempomat](https://tempomat.dev) is a small macOS utility to monitor CI pipelines, the requirements are fairly simple:

- I needed to create an app icon, with all the size variations needed to publish an app to the app store (in this case macOS icons)
- Every once in while I need to add custom icons, I am by no means a designer, so I try to stick to simple shapes/icons I can easily replicate or sometimes use placeholder art from sites like the noun project and then replace them with my own versions.
- I also need to generate marketing material and app store artwork, if you constantly update your product generating this can be cumbersome at least

I'm a big believer of the KISS principle, so I basically use 2 tools, Figma and a small script to generate icons, here is a screenshot of current file I have:

![Tempomat Figma]({{site.url}}/assets/tempomat/1.JPG "Tempomat figma")

It is pretty minimal and I already cleaned it up a bit for this article, but I intentionally try to keep it as simple as I can, so let's go by parts

## App Icon
I won't show you how many iterations I went through until I reached the current app icon, but Figma is great for this, it is super simple, yet provides you with a way to achieve almost anything you might need for an icon, you could do the same thing in sketch but the benefit of Figma is that it's free, if you need collaboration then it is also the ultimate tool to run the job!

![Tempomat Icon]({{site.url}}/assets/tempomat/2.JPG "Tempomat Icon")


I create the frame with a 1024x1024 size and just work on top of that, duplicating the frame as I go trying ideas and variations, once I'm happy with the result I right click copy as png and then paste it again so I don't have to worry about funny scaling issues when resizing the icon in the artwork.

Afterwards I export the full 1024x1024 icon as a PNG and I use the [ios-icon-generator](https://github.com/smallmuou/ios-icon-generator) script that I found on github, there are many web tools that can do this for you, but they are all bug fest/ads mess, just point the script to the input file and where you want to drop the generated files and enjoy:

`./ios-icon-generator.sh myIcon.png iosIcons/`

## Other Icons
Tempomat integrates with 3rd party CI systems so I just find a svg representation of the company logo and drop it right into figma, sometimes I might do small modifications to make the icon look nice within the app, then I can quickly modify colors which are used for representing the status of a branch/repo

![Other Icons]({{site.url}}/assets/tempomat/3.JPG "Other Icons")

## Artwork
This one is by far the biggest time saver, for the macOS app store art, the resolution is not the same as the macbook (my macbook model?), so at first I fumbled around trying to make screenshots fit the asked resolution, until at some point I just gave up and realized I was just wasting my time, I just create a frame with the necessary resolution (in this case 2880x1800), then I can put the any screenshot I need in there, make it fit, put some promotional text or w/e.

I also made a component of this small repeated pattern, so I only have to adjust it once to generate more artwork for social media, different platforms, etc. it's pretty handy

![Artwork]({{site.url}}/assets/tempomat/4.JPG "Artwork")


## When Prototyping the most important thing is Funtionality
Form follows function, Dieter Rams said it, so I actually heavily discourage using Figma for prototyping ideas, I loose focus of the important things, I really couldn't care less about paddings and margins, they are important in the final product, but I'm a strong believer of sketching rough ideas on an iPad or a piece of paper (a la [shape-up](https://basecamp.com/shapeup)) but then building a ugly but functional code prototype, I can iterate 20 times quicker with hard coded values and interact with real code without having to do some presentation with figma frames (which is possible but I don't like it)