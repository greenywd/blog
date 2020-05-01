---
layout: post
title:  "Apple TV 4K Recovery Mode"
date:   2020-05-01 20:00:00 +0930
categories: [work, apple]
---
Let me preface by saying that the Recovery Mode that I found (I'm sure there's some other recovery mode somewhere in tvOS), doesn't let you do anything but Reset All Settings and Restart. It doesn't let you restore from say a firmware file, but in my case it did what it needed to do.

Another work story that happened quite a while ago, but I was reminded of today. We had to put up a heap of new Apple TV 4K's around the place, and the configuration for all but one went flawlessly. This one Apple TV, refused to go past the remote management setup - I can't remember the exact error, but it was something along the lines of the configuration profile being invalid. The configuration profile was definitely valid, as the rest of the Apple TVs didn't have an issue with it.

So, we had this one Apple TV in our office that could not get past the setup screen because it thinks the configuration profile is invalid. My first thought was to see if we could reset it, something similar to previous Apple TVs that you could plug into a Mac and restore their firmware. Unfortunately, the Apple TV 4K lost the USB-C port and [Apple's support article][restore-appletv] says to contact support to restore an Apple TV 4K. I assume we'd end up with a replacement one way or another but me being me, I wanted to see if there was another way. 

![Apple TV Recovery Mode][appletv-recovery-image]
Image from /u/Jar30002 on their [Reddit post][appletv-recovery-reddit] about Recovery Mode

I believe you can get into the Recovery Mode once the Apple TV has been setup (not that it's very useful) through a combination of button presses, but as this one Apple TV hadn't finished setting up that didn't work. Luckily, I came across a [comment on a Reddit thread][appletv-recovery-process-reddit] which put me on the right track. The exact instructions given by the commenter didn't work for me, but unplugging the Apple TV from power, waiting a second, plugging it back in and repeating multiple times worked. Your mileage may vary, but I found I had to unplug completely from the power outlet, instead of turning the switch on and off.

And to my surprise, I was greeted with the recovery screen where I was able to reset the Apple TV's settings and start the configuration process again. Luckily, this time it went through the configuraiton like the rest of the Apple TVs did in the first place.

[restore-appletv]: https://support.apple.com/en-us/HT203028
[appletv-recovery-image]: {{site.baseurl}}/assets/appletv-recovery-mode.jpg
[appletv-recovery-reddit]: https://www.reddit.com/r/appletv/comments/7namlt/have_been_getting_this_more_and_more_frequently/
[appletv-recovery-process-reddit]: https://www.reddit.com/r/appletv/comments/7namlt/have_been_getting_this_more_and_more_frequently/