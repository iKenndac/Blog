---
author: Daniel Kennett
date: '2010-10-04 12:05:25'
layout: post
slug: the-store-is-dead-long-live-the-store
status: publish
title: The store is dead. Long live the store!
wordpress_id: '613'
categories:
- Programming/Work
---

Many moons ago, I sold two programs: Writer (a little word processing
app) and PodUtil 2.0 (which evolved into my current app, Music Rescue).
I'd decided to sell them through the payment processor
[eSellerate](http://www.esellerate.net/). However, eSellerate worked in
dollars and my bank charged £20 to deposit a foreign cheque. That was
approaching 10% of my approximate monthly income of $400! Things had to
change.

My bank had a credit card processing facility available to business
customers, which was cheaper than eSellerate *and* worked in Pounds
Sterling *and*deposited the money straight into my account. Perfect!

"Sorry, sir, you have to be 18 years old to open a business account," I
was told. The day after my eighteenth birthday I went over the there and
applied for their service. Soon after I had my own little PHP page that
forwarded customers to a HSBC-branded page that took their details, and
upon a successful transaction forwarded them back to another PHP page of
mine that would give them a license code.

In 2005, I'd been deemed trustworthy enough to use HSBC's XML API. This
was beyond my PHP abilities, so I bought an Xserve G5 (obviously) to
host WebObjects applications and wrote a store in that.

![Xserve Setup](http://danielkennett.org/wp-content/uploads/2010/10/P1010056.jpg)

Finally, customers could buy my apps from my own site without the
jarring disconnect of going to HSBC to pay! Over the years that
WebObjects application has evolved to accept PayPal and so on, but it's
more or less the same application I wrote in 2005.

On Monday, October 4th 2010, at 6:04am UTC, that store sold its last
license. I'd like to observe a moment of silence for the deceased…

![Store Down](http://danielkennett.org/wp-content/uploads/2010/10/store_down.png)

### A Steady Decline

So, why the switch? Well, I've detailed reasons why a full-on payment
service (rather than a basic gateway where you roll your own store) is
beneficial
[before](http://www.kennettnet.co.uk/blog/comments/the_great_debate/).
However, at the time I wrote that my WebObjects store was working well
enough to leave it alone. However, recently, my relationship with both
WebObjects and my payment processor (my bank, HSBC) has been going
downhill.

• WebObjects (on my machine, at least) is stable enough for just long
enough for me to stop checking on it every day. Then, it'll fall over
for some reason and the only way to fix it is to reboot the machine. A
few months ago I lost four days of sales due to this happening when I
was away from an internet connection.

• The novelty of having my own server sitting in a data-centre in London
has worn off. I'm in constant worry of it failing, and now I'm in Sweden
it'll be an *enormous* pain in the ass getting it going again, and I
can't be bothered to figure out how to deploy WebObjects on something
else. I've already got a [Linode](http://www.linode.com/) account
running my email, this blog and half of kennettnet.co.uk, and I'll be
moving the rest over in the coming weeks.

• HSBC is not geared for selling electronic products. They refuse to
fight chargebacks because I've no physical proof of the product being
delivered (email logs aren't enough) and have started fining me
£20/month because I won't pay for an expensive "security review" to make
sure I'm not letting credit card details out to a bunch of hackers.
Never mind that I never store credit card details on my hardware at all
— they get sent off to the HSBC API and forgotten before the result
comes back — I still need a review. Because I've got better things to do
with my time and money, I'm getting charged £20/month and they "may stop
doing business with me in the future". Yeah, not if I leave first.

### Jumping Ship

I was quietly simmering about HSBC and my crappy store about a month ago
when Realmac released Courier. I downloaded it and checked it out, and
noticed that it had a built-in store that looked pretty darn awesome. I
ended up signing up for a trial account with their processor,
[FastSpring](http://www.fastspring.com/).

I'm going to come out and say it: FastSpring is *awesome*. I haven't
experienced customer service this good in my life. Every query I've had,
from stupid questions to difficult questions to bug reports has been
dealt with brilliantly.

• **Can I load my entire order history into your system in order to
allow automatic discounts for existing customers?** *No. However, there
are a few ways to do what you want to do — here's what another customer
of ours have done. If these don't work, get back to us and we'll see
what else we can do.*(Their suggestion worked perfectly)

• **What character set do names get passed into the license generation
script I wrote? I need to ensure accented characters and such work
properly.***This doesn't work well at the moment, but we've an idea or
two to make it better.*(After a discussion with them, it appears we've
found a good solution that they'll hopefully implement soon. In
practice, this isn't actually tuning out to be much of a problem)

Not only is their customer service great, but their product is brilliant
as well. I've actually been *enjoying* setting everything up and
building embedded stores in my applications.

The *one* thing that isn't idea is that their base currency is US
Dollars. However, the ability to charge the customer in their native
currency in a friendly and embedded way and to not have to worry about
VAT again far, far outweighs the fluctuations I'll see in exchange rates
— although I may reconsider if the USD falls to 2 to the £ again!

![Clarus Embedded Store](http://danielkennett.org/wp-content/uploads/2010/10/ClarusStore.png)Clarus'
Embedded FastSpring Store

In a way, I'm sad to see my WebObjects store go — it was written because
I had a successful product that needed a professional-looking store.
However, I stop feeling sad when I remember that I'm moving to
FastSpring because my products are successful enough to be able to trade
slightly more expensive payment processing for a better customer
experience.

Long live the store!
