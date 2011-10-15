---
author: Daniel Kennett
date: '2010-09-10 15:48:14'
layout: post
slug: simcity-nerds-and-nasa
status: publish
title: SimCity, Nerds and NASA
wordpress_id: '600'
categories:
- Sweden
---

![Twitter](http://danielkennett.org/wp-content/uploads/2010/09/Twitter.png)A
few days ago, I wrote
[this](http://danielkennett.org/blog/2010/09/a-perfect-analogy-between-swedish-and-british-communication-and-travel/)
post about the underground trains in London and Stockholm. This sparked
the conversation you see to the left on Twitter.

SimCity!!! I *love* SimCity. I used to play it loads, but haven't had
the chance to in a long time. I have the game installed on my Mac, but
have lost the disc. After obtaining the disc again through *completely
legitimate means*, I remembered why I stopped playing — SimCity 4 on the
Mac is slooooooow.

Eventually, I bought the PC version for £10 and started playing. I saw
that the game came with regions to play on that match real-life areas —
London, San Francisco, New York, etc. Wouldn't it be fun to build a
SimCity on a region that matches Stockholm? Yes, it would.

After searching for a while, it became apparent that I wasn't going to
find one. Then, I stumbled upon a page [describing how to create SimCity
4 regions from a greyscale elevation
model](http://www.sc4ever.com/knowledge/showarticle.cfm?id=1103).

Superb! All I'd need to do is find an elevation model of the Stockholm
area and I'd be set! My search eventually led to the [ASTER project](http://en.wikipedia.org/wiki/Advanced_Spaceborne_Thermal_Emission_and_Reflection_Radiometer)
then to NASA's [ASTER GDEM](http://asterweb.jpl.nasa.gov/gdem.asp)
(Global Digital Elevation Model) site. After following an *[incredibly simple](http://asterweb.jpl.nasa.gov/gdem-wist.asp)* order process and
waiting a few hours, I had my data!

Problem is, the ASTER satellite data simply isn't accurate enough for my
*incredibly demanding* needs, and the data I managed to get wasn't good
enough. In the screenshot below, I've written "Stockholm" on the map
approximately where Google Maps puts it at the same zoom level. The map
shows the Stockholm city area and surrounding suburbs.

![NASA ASTER GDEM](http://danielkennett.org/wp-content/uploads/2010/09/Map-NASA.jpg)

So, now what? Eventually, I turned to Google Maps. The standard and
terrain maps, while lovely and clean, are covered in roads and labels.
The satellite picture shows the water-covered areas fairly cleanly (a
few clouds notwithstanding), so while it wouldn't give me a
height-accurate SimCity region, I'd at least get one with the lakes and
stuff in the right place, which is good enough for a game of SimCity.

I suppose.

So, this is what Google Maps' satellite image gave me for the region:

![Satellite Map](http://danielkennett.org/wp-content/uploads/2010/09/Map-Sattelite.jpg)

Using Photoshop, I manually selected all the water with the Magic Wand
tool, and saved that selection. Then, I created a layer of flat 25% grey
(just below sea level in a SimCity elevation model), and another one of
flat 40% grey (just above sea level). Using the earlier selection, I
punched a hole in the 40% grey to show the 25% grey underneath. The
result:

![Map-Final.jpg](http://danielkennett.org/wp-content/uploads/2010/09/Map-Final.jpg)

With that made, I followed the instruction on the page linked earlier to
create a SimCity region. After fifteen minutes of data crunching as I
experimented with getting the right scale, SimCity finally gave me this.
Hooray!

![SimCity Map of Stockholm](http://danielkennett.org/wp-content/uploads/2010/09/Map.jpg)

If you compare it with Google's terrain map of the same area, you'll see
that apart from some jaggy edges on the lakes (which can be smoothed out
in-game), it matches pretty well with the geography of the area:

![SimCity Map with Google Overlay](http://danielkennett.org/wp-content/uploads/2010/09/Map-with-Overlay.jpg)

All this only took about four hours. Now I can finally play my game!
