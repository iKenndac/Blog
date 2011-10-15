---
author: Daniel Kennett
date: '2010-04-09 14:04:05'
layout: post
slug: moonlighting-in-net-part-2-what-no-mvc
status: publish
title: 'Moonlighting in .NET Part 2: What, no MVC?'
wordpress_id: '544'
categories:
- Programming/Work
---

I’m a Cocoa developer first and foremost, but for the next few months
I’ll be moonlighting as a C\#.NET developer, writing version 5.0 of my
Music Rescue application from scratch. I actually have version 4.0 in
Visual Basic.NET, but, you know — Visual Basic is for chumps.

Writing in C\#.NET is an… interesting experience for someone used to
Objective-C. This series of posts will discuss .NET from the perspective
of a Cocoa developer — what’s good, bad, and just different.

The biggest day-to-day difference between Cococa and .NET is that, by
default, you *don't use MVC*. To any Cocoa developer, the thought of not
using the MVC (Model-View-Controller) pattern to build an application
should be absolutely horrific. In fact, try and build a simple Cocoa app
in Xcode without using MVC - it's *really* hard. I've honestly no idea
why .NET/Visual Studio/etc defaults to this approach.

### The Status Quo

Visual Studio, by default, strongly encourages the use of Code Behind in
the way Xcode strongly encourages MVC. When you create a window, the IDE
creates a subclass of Window for you and you start adding controls to
it. The events for controls (button clicks, etc) are also placed in this
Window subclass by default. In the IDE, the window and the code are
treated as separate items, but they get compiled down to the same class
when the application is compiled.

This produces a huge problem if you want any kind of flexibility, or
want to localise your windows and views - since the window/view and
controller code are the *same thing*, you can't just load in a different
window/view tuned for display in whatever language you'd like.

### Fixing It

Since .NET provides no built-in MVC classes, I ended up writing my own
window and view controller classes in
[KNFoundation](http://bitbucket.org/ikenndac/knfoundation/), which
provide the controller part of the model-view-controller pattern. They
provide the standard window/view controller features as provided in
Cocoa:

-   When initiated, they look for localised versions of the given
    view/window name, and load in the correct one.
-   Controls placed in the view/window are automatically connected to
    properties in your controller subclass if they're present.

They also look for a localised strings table with the same name as the
view/window and attempt to apply it to the loaded view/window. See the
[Localizing SparkleDotNET](http://bitbucket.org/ikenndac/sparkledotnet/wiki/Localizing)
page for an example of this at work. This is handy if you'd like to
localise an item's strings but not the whole item, and is inspired by
[this post](http://wilshipley.com/blog/2009/10/pimp-my-code-part-17-lost-in.html)
by Wil Shipley.

If you're a .NET developer and would like to try this out, check out my
open-source KNFoundation library.

Getting the Visual Studio IDE to play along with this isn't too hard,
but it is a bit tedious. Every time you create a new window or view, you
need to remove the "Class" attribute from the created XAML (which is
equivalent to an XIB) file to stop .NET resolving the XAML file to a
class. Next, you tell Visual Studio not to compile the XAML file, but to
copy it to your application's resources directory instead. Finally, you
delete the generated code behind file. You only have to do this once per
XAML file, but since XAML files can't contain more than one item (view,
window, etc), this gets old fast! TIme to create a custom file template,
I guess.

Loading this XAML file to a window or view is fairly simple - use the
built-in XamlReader class to load in the XAML file and you'll be given
back a Window or UserControl object to start working with.

**Next time:**WPF, the jewel in .NET's crown.
