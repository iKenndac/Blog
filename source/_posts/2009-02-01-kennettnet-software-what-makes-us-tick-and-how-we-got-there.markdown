---
author: Daniel Kennett
date: '2009-02-01 16:27:12'
layout: post
slug: kennettnet-software-what-makes-us-tick-and-how-we-got-there
status: publish
title: 'KennettNet Software: What Makes Us Tick And How We Got There'
wordpress_id: '203'
categories:
- Programming/Work
---

Every programmer has a plethora of tools up their sleeve to make their
job more about programming and less about managing the files and issues
that come about. I thought I'd share the tools that make up our
workflow. 90% of the time all our work is done in our office and at the
moment, projects are rarely worked on by more than one person. The
Windows version of Music Rescue 4.0 was a bit different, but the bits I
worked on conveniently fit into frameworks that could be used by the
main app. The other 10% of the time ((Although at the moment the ratio
seems to be 90% at home and 10% at the office.)) I'm working either at
home on my iMac or on my travels on my MacBook. **Design**
![acorn](http://danielkennett.org/wp-content/uploads/2009/02/acorn.png "acorn")I
often use
[OmniGraffle](http://www.omnigroup.com/applications/omnigraffle/) and
[OmniOutliner](http://www.omnigroup.com/applications/omninoutliner/) to
make diagrams of processes and lists of... things, and I'm a big fan of
Omni in general. ((Though it was better when Wil Shipley was there))
However, normally nothing beats good old pencil and paper. I have
several sketchbooks filled with sketches for various projects - these
days, one or more per project. When I move to the computer, I use
[Acorn](http://flyingmeat.com/acorn/) for basic image editing and
Photoshop for advanced stuff. Acorn really is a great little image
editor - it's getting rarer and rarer that I use Photoshop for making
interface graphics. **Coding** Our IDEs are fairly simple affairs. For
writing Cocoa programs, we use the latest versions of Xcode and
Interface Builder. For WebObjects apps, we use Eclipse and for .NET apps
we use Visual Studio 2005 in Parallels. No custom editors or anything
like that here. **Version Control** We're actually fairly new to
"proper" version control. Music Rescue 3.x was written in REALbasic,
which stores the entire project in a single file. Every version released
I'd create a backup of the project file - more often when working on big
upgrades. For our WebObjects and .NET projects I'd just backup the
folders containing the projects.
![bazaar](http://danielkennett.org/wp-content/uploads/2009/02/bazaar.png "bazaar")During
the development of Music Rescue 4.0, we finally realised that we needed
something better. After researching many of the systems, we came across
[Bazaar](http://bazaar-vcs.org/). It provides the ability to have local,
folder-based repositories for simple projects, and distributed
repositories for the larger projects that I need wherever I am. It's
lovely and simple, and although there's no decent front end for it for
the Mac, the command line version is simple enough for that to not
really matter. There's an excellent overview of Bazaar
[here](http://www.mcubedsw.com/blog/index.php?/site/comments/version_control_with_bazaar/)
on M Cubed Software's blog. **Issue Tracking** Our issue tracking for
Music Rescue 3.x was a text file called "To-Do" in the folder for each
version's project file. After that and a pen and paper both proved to be
worthless, we experimented with publicly accessible web apps - first a
normal forum where users could come and report their problems, then a
specialised app called [The Bug Genie](http://www.thebuggenie.com/),
still up at
[http://bugs.kennettnet.co.uk/](http://bugs.kennettnet.co.uk/).
![lhkbanner](http://danielkennett.org/wp-content/uploads/2009/02/lhkbanner.png "lhkbanner")Neither
of those went well - the forum was too general and The Bug Genie is too
complex. After Music Rescue 4.0 was released, a fellow developer
mentioned on Twitter that he was developing a front end to the online
issue tracker called [Lighthouse](http://www.lighthouseapp.com/). I had
a look and their tagline instantly hit home - "Beautifully simple issue
tracking". After investigation, Lighthouse gave exactly what we needed -
a service (albeit one that costs money) accessible from anywhere
dedicated to issue tracking that's simple and easy to use. M Cubed's
[Lighthouse Keeper](http://www.mcubedsw.com/software/lighthousekeeper)
is a wonderful front end that we can use to manage our projects' issues.
**Customer Support** For customer support, we use Mail that ships with
Mac OS X. It isn't very good, and I'm starting to look for better
alternatives. **Web Development**
![coda](http://danielkennett.org/wp-content/uploads/2009/02/coda.png "coda")I
used to use Dreamweaver, but it sucks. Fortunately,
[Panic](http://www.panic.com/) released
[Coda](http://www.panic.com/coda/), and I no longer have to beat my head
against the wall every time I need to update a bit of website. That
said, Dreamweaver is handy for when I'm too lazy to write the HTML for a
big table or can't remember how to make a drop-down menu, but other than
that it gets launched rarely enough to get relaunched straight away by
Adobe Updater. Sigh. For the times I'm just uploading images or scripts
or whatever, Panic again makes life easy with
[Transmit](http://www.panic.com/transmit/). Basically, Panic == win. I
miss Audion. If you want a genuinely interesting insight into Mac
software development, read [Audion's story](http://www.panic.com/extras/audionstory/) on their website. It's
a brilliant read. **Other**
![screenrecycler](http://danielkennett.org/wp-content/uploads/2009/02/screenrecycler.png "screenrecycler")At
work, I use a Mac Pro with two 23" displays attached to it. When away I
use a 13" MacBook. At home I have 24" iMac, but miss the dual screen
setup. The solution? [ScreenRecycler](http://www.screenrecycler.com/),
an application that "fools" your Mac into seeing a second screen that's
actually the app hosting a VNC server. Connect to it from another
machine and that machine becomes a secondary display! Over a wireless
.11n network it's not quick enough to play video but it's certainly fast
enough to do programming work on! Here's a photo of my home working
environment using ScreenRecycler and my MacBook as a secondary display
(click for a larger view): [![Home setup with ScreenRecycler](http://danielkennett.org/wp-content/uploads/2009/02/img_4470-300x199.jpg "Home setup with ScreenRecycler")](http://danielkennett.org/wp-content/uploads/2009/02/img_4470-1024x680.jpg)
When I started writing this post I could only remember a couple of apps
that I used on a daily basis, until I started actually bringing up some
of them as I worked. I didn't realise how many there were, and how many
are from independent software developers like us. I'm glad I've
contributed to the market I'm trying to make a living in!
