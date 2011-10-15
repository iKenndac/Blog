---
author: Daniel Kennett
date: '2010-03-09 20:57:52'
layout: post
slug: moonlighting-in-net-part-1-living-in-a-bubble
status: publish
title: 'Moonlighting in .NET Part 1: Living in the Bubble'
wordpress_id: '531'
categories:
- Programming/Work
---

I'm a Cocoa developer first and foremost, but for the next few months
I'll be moonlighting as a C\#.NET developer, writing version 5.0 of my
Music Rescue application from scratch. I actually have version 4.0 in
Visual Basic.NET, but, you know — Visual Basic is for chumps.

Writing in C\#.NET is an… interesting experience for someone used to
Objective-C. This series of posts will discuss .NET from the perspective
of a Cocoa developer — what's good, bad, and just different.

.NET is implemented independently from the OS, which can be a
double-edged sword. On the plus side, you get all the features of the
new framework on Windows XP (wouldn't you love Core Animation on 10.1?),
but on the negative side, the ritzy new features in Windows Vista and 7
(such as [Glass](http://en.wikipedia.org/wiki/Windows_Aero) or
in-taskbar progress bars) aren't included in all but the latest .NET
versions (not the versions that ship with each OS) — you have to Interop
down to Win32 to use them. While Microsoft does provide wrapper classes
for these features as a separate download, it does dull the experience
in what's supposed to be a cutting edge, modern framework.

### The CLR

This time, I'm talking about a huge part of .NET — the Common Language
Runtime, or CLR. The CLR is similar to Java's VM in that .NET apps,
whether they're written in C\#, Visual Basic or something else all get
compiled down to a common bytecode that is then translated to the target
CPU at runtime. This means that all .NET applications are kept in their
own little managed, garbage collected bubble, safe from the atrocity
that is the Win32 API.

Microsoft have used this opportunity to create an interesting set of
security features — much like Java, your application can have its access
to the disk and various other system resources limited based on settings
made by an administrator. Normally, this isn't a problem — however, if
you're not very defensive about what you're doing with these resources,
expect to get a ton of crash reports the first time a user tries to run
your application from a network mount.

Finally, compared to the Objective-C runtime, .NET's CLR is *very*
static. No sending messages to nil objects and no swizzling or any of
that cool stuff. Want to dynamically swap a method implementation with
another one to, say, use your own custom implementation of KVO on other
objects? Nope, not gonna happen.

### Talking With The Rest Of The System

Unfortunately, even with .NET 4.0 (which is currently at Release
Candidate status), using .NET is like being back in the Mac OS X 10.4
days where you had to dip down into Carbon all too often — you won't be
going long until you have to make a call through to Win32. Fortunately,
.NET includes the System.Interop namespace, letting you call through to
standard DLLs with ease. However, this does expose you to some of the
peculiarities of Win32 - for example, to register for notifications on
device changes, you need a *window* handle — something I didn't have to
hand in my DLL, and I ended up having to create an invisible window to
accomplish this.

Interop becomes even more difficult when you need to pass pointers
around. Since the CLR is an opaque lump of memory to the rest of the
system, you can't pass a pointer to something outside of the runtime.
When passing "stack" variables directly, Interop does this for you, but
if the call will be, say, filling a struct, the process is a little more
involved:

• Allocate the struct in your managed code.

• Using System.Interop, copy the chunk of memory over to the unmanaged
memory space where the rest of the system can get at it, which gives you
a pointer in return.

• Call the Win32 API you want, passing the given pointer as normal.

• Using System.Interop, copy the chunk of memory back into the managed
memory space where you can access it from the CLR.

• You're done! Since the unmanaged memory space isn't garbage collected,
don't forget to deallocate the memory space you copied to.

Here's a nice diagram of what's going on:

![CLRDiagram](http://danielkennett.org/wp-content/uploads/2010/03/CLRDiagram.png)

Or, in terms of code:

**Objective-C**

    [cc lang="c" escaped="true"]struct MyStruct myThing;
    ASystemCall(&myThing);[/cc]

**C\#/.NET**

    [cc lang="c#" escaped="true"]
    MyStruct &myThing;
    int inputSize = Marshal.SizeOf(GetType(MyStruct));
    IntPtr ptr = Marshal.AllocHGlobal(inputSize); // Allocate some memory
    Marshal.StructureToPtr(myThing, ptr, true); // Copy our struct into it
    ASystemCall(ptr); // Call the method
    myThing = (myThing)Marshal.PtrToStructure(ptr, GetType(MyStruct)); // Copy the structure back
    Marshal.DestroyStructure(ptr, GetType(MyStruct)); // Deallocate the unmanaged memory
    [/cc]

### **Is It Worth It?**

Even though the CLR does impose some serious limitations at times, from
the pain-in-the-ass interop with the rest of the system and the
limitations imposed on your code when you're not running from a
"trusted" location, the .NET CLR **is**pretty awesome. For the most
part, you're shielded from Win32 and its problems (mainly due to the
fact that Win32 is decades old and full of cruft and old conventions),
and Microsoft have really done a great job in starting from scratch to
build a modern object-oriented framework.

**Next time:**Wot, no MVC?
