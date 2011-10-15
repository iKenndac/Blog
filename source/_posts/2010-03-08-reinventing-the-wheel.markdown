---
author: Daniel Kennett
date: '2010-03-08 11:22:52'
layout: post
slug: reinventing-the-wheel
status: publish
title: Reinventing the Wheel
wordpress_id: '522'
categories:
- Programming/Work
---

Over the past week or two, I've been working exclusively in Visual
Studio on Windows, writing the core components of the next version of my
Music Rescue application.

I've been fairly vocal on Twitter about my experiences, from bitching
about C\# to actually hailing how good the experience is compared to
WinForms and .NET 2.0. What seems to have got a lot of attention,
particularly from .NET developers, is the fact that I'm reimplmenting a
portion of Cocoa's Foundation framework in .NET. People don't seem to
see the point, and I've been asked why I'm not using the stuff built in
to .NET instead.

In this post, I'm going to talk about why I'm reimplementing bits of
Cocoa in .NET, and why I'm doing it this way around instead of
implementing bits of .NET into Cocoa.?

It's All About Cross Platform

This effort is for [Music Rescue](http://www.kennettnet.co.uk/products/musicrescue/), the
application I write for both Mac and Windows. The application is largely
the same on both platforms, but not written in a "common" language that
will compile for both platforms like
[REALbasic](http://www.realsoftware.com/realbasic/), or using a project
to allow one framework to be used on another platform like
[Mono](http://www.mono-project.com/) or
[CocoTron](http://www.cocotron.org/). The reason for this is simple -
much like using Java, using these tools doesn't allow you to make
beautiful applications on the target platform - you simply end up with
something that looks poor on both.

So, Music Rescue on the Mac is written in Cocoa/Objective-C, and on
Windows is written against .NET using Visual Basic for the current 4.x
version, and C\# for the upcoming 5.x version. This allows me to achieve
an application that completely fits in to whichever platform you're
using it on.

However, Music Rescue does need to be able to share resources and such.
For example, the application can optionally save your license and other
settings to your iPod or iPhone, so when you use Music Rescue with your
device on another machine the app will automatically pick up your
settings. For this, I need a settings file that's readable on both
platforms.

**Why Cocoa in .NET?**

Much of the decision is simply that I'm more familiar with Cocoa.
However, before choosing to implement a piece of Cocoa in .NET, I
research .NET's built-in functionality first before choosing to
implement something in .NET rather than in Cocoa. Most of the time, the
functionality is either not there or the Cocoa way of approaching things
is *much better.*

**A Complex Example - Localisation**

Cocoa's approach to localisation is pretty simple - your application's
package contains one or more folders called <Language\>.lproj,
containing your localised resources. A class called NSBundle lets you
very simply find a localised resource, and 99% of the time in your app
you don't have to write localisation code - just ask for a localised
resource or string and NSBundle will find the correct localised resource
or string, and fall back to other, more general localisations if they
exist.

This set-of-files approach is different from the approach .NET takes, as
far as I can see - .NET seems to want to embed strings tables and
resources in your application executable. This *does* have the advantage
of ensuring your localisations won't get lost or tampered with, but,
actually, I *want*users to be able to be tamper with my localisations.
Why? Because using Cocoa's approach, users need *nothing but your
application and a text editor*to completely translate your application
into a new language. They simply duplicate the English.lproj folder (or
whatever), rename it French.lproj (or whatever) and edit the .strings
and .xaml (for .NET) files using Notepad. When they relaunch the app -
BAM - it's in French.

This is an absolutely fantastic way to get people to localise your app.
They don't need complex and potentially expensive localisation tools,
and the application doesn't need to be made aware that the new
localisation exists - it finds the new folder automatically and uses the
localisations there.

**Oh, and Money, Of Course**

A small but important part of this localisation example is that my
implementation of NSBundle and its localisation features is using
exactly the same file format as Cocoa's native implementation does. This
means a ton of saved time and money for me as at least 90% of the
localised strings are the same in the Mac and Windows versions of my
app, and I can literally use the same file on both the Mac and Windows
versions.

**Roaming Installations**

Finally, implementing all this has given an unexpected bonus - I can
ship a Mac and Windows "virtual" universal binary that allows both the
Mac and Windows binaries to share literally the same resources, and
appear to the user as a single application on either platform. Now, I'm
aware this is a very limited scenario, but for version 5.0 of Music
Rescue I want to support roaming installations again - this allows the
user to install both the Mac and Windows versions of the app onto their
iPod so they can use Music Rescue wherever they are. Having both
applications share literally the same resources will practically halve
the download size and storage costs of such an installation.

**What have I actually ported across?**

Well, not that much from Foundation, to be honest. I *have*implemented a
version of Cocoa's table view in .NET as well as a few other smaller
controls, but the reasons for that should be obvious to anyone who's
tried to use .NET's built-in table view.

• **NSKeyValue(Coding/Observing)**An implementation of the observer
pattern that Cocoa uses.

• **NSBundle** As discussed above, this provides an implementation of
the localisation model that Cocoa uses so I can share localisations
between the two applications.

• **NSNotificationCentre** An implementation of the notification pattern
that Cocoa uses.

• **NSPropertyListSerialization** This is an implementation of Cocoa's
property list reading and writing, to allow cross-platform sharing of
settings files without having to write some custom XML thing on both
platforms.

• **NS(Window/View)Controller** Helper classes to implement the
model-view-controller pattern in WPF/.NET. Integrates with my NSBundle
implementation to automatically load the correct localised window or
view.

**"Fighting the Framework"?**

Most people have simply asked me why I'm implementing bits of Cocoa in
.NET, which is fine and understandable - hopefully this post has
answered that a bit. However, I was asked a while ago why I'm "fighting"
.NET by implementing Key-Value Observing and Key-Value Coding - the
assertion of the argument was that as .NET doesn't provide this I
shouldn't try to use this pattern at all.

I hope that anyone who has done a decent Computer Science degree
realises how dumb that sounds. Patterns like observation (or factory
classes, or shared instances, or model-view-controller, or...) are
simply ways of approaching a particular task, and to suggest that
because a particular framework doesn't include a (decent) implementation
of a pattern you shouldn't use it at all is simply baffling to me. The
idea that I'm *fighting*.NET by implementing an observation pattern is
even worse - since when is adding functionality "fighting"?


