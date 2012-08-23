---
layout: post
title: "Go Native or Go Home"
date: 2012-08-22 10:48
comments: true
categories: iphone, ios, android, flash, tryios, codeschool
published: true
---

Flash, the once poster-child of the mobile cross-platform cabal, is finally [dead on android][flash].  A little over 2 years ago Steve Jobs' wrote down his [Thoughts on Flash][thoughts], a reasonable attempt to explain to the programming world why the iPhone and iPad did not ship with Flash.  And looking back, he was right: Flash wasn't ready.  It never become "ready", even 2 years later.  

Jobs' wrote down *six* reasons why iOS didn't have Flash, and much ink was spilled by tech writers at the time over the first five.  Whether or not Flash interfaces worked with touch screens, the use of Flash for video, whether Flash drained battery, security, performance, the "openness" of Flash, etc.

But the sixth reason, by Jobs' own admission, is the most important one.  Apple didn't want developers on their platform to use Flash to build apps.  Here, in his own words:

> We know from painful experience that letting a third party layer of software come between the platform and the developer ultimately results in sub-standard apps and hinders the enhancement and progress of the platform. If developers grow dependent on third party development libraries and tools, they can only take advantage of platform enhancements if and when the third party chooses to adopt the new features. We cannot be at the mercy of a third party deciding if and when they will make our enhancements available to our developers.
>
> This becomes even worse if the third party is supplying a cross platform development tool. The third party may not adopt enhancements from one platform unless they are available on all of their supported platforms. Hence developers only have access to the lowest common denominator set of features. Again, we cannot accept an outcome where developers are blocked from using our innovations and enhancements because they are not available on our competitor’s platforms.

This still holds true today.  Whether you use [PhoneGap][gap], [AppCelerator][appcel], or even [RubyMotion][motion], you are relying on a third party to supply you with the developer tools for a platform they don't control.  In RubyMotion's case, you can take some comfort that they only support iOS and thus won't fall into cross-platform least-common-denominator purgatory.  But you can still find yourself in the situation where RubyMotion, or whatever framework you use on top of RubyMotion, falls behind the APIs developed by Apple.  

But the tug of the iOS platform is [strong](http://www.inquisitr.com/252304/apple-announces-30-billion-app-downloads-5-billion-paid-to-developers/), and it's tempting to take the PhoneGap or AppCelerator shortcut, and just write your App in HTML+CSS+Javascript.  Don't.  Take some time [learn how to write iOS applications using Objective-C][kick].  

It's not as hard as you think.  Don't let your overzealous pattern-matching reflex blind you to the fact that just because smartphones *are* computers, people will be *okay* with sub-standard, cross-platform web apps. They are slow and don't take advantage of the richness of the phone's capabilities and speed.  You *sit down* at your computer, so a few hundred milliseconds here and there are no big deal.  People expect more out of the computer that goes everywhere with them (even to bed).  It needs to be an extension of themselves.  A couple hundred milliseconds of lag is not acceptable on a smartphone.  Facebook found that out [the hard way][fb]:

> So while utilizing web technology has allowed us to support more than 500 million people using Facebook on more than 7000 supported devices, we realized that when it comes to platforms like iOS, people expect a fast, reliable experience and our iOS app was falling short. Now that our mobile services had breadth, we wanted depth. So, we rewrote Facebook for iOS from the ground up (I really did open up Xcode and click "New Project") with a focus on quality and leveraging the advances that have been made in iOS development.

This is why I want to create [awesome iOS development learning resources][kick] so there will be no excuse left not to create native applications for iOS.

[flash]: http://blogs.adobe.com/flashplayer/2012/06/flash-player-and-android-update.html
[thoughts]: http://www.apple.com/hotnews/thoughts-on-flash/
[appcel]: http://www.appcelerator.com/
[gap]: http://phonegap.com/
[motion]: http://www.rubymotion.com/
[fb]: https://www.facebook.com/notes/facebook-engineering/under-the-hood-rebuilding-facebook-for-ios/10151036091753920
[kick]: http://www.kickstarter.com/projects/eallam/try-ios-iphone-app-development-course