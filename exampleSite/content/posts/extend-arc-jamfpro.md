---
title: More boost with Arc for Jamf Pro
date: 2023-11-02
description: "Utilise Arc Boosts with JavaScript to streamline and enhance multi-instance Jamf Pro management."
image: https://share.cleanshot.com/npR9vjZq+
tags: ['arc', 'jamfpro', 'boost']
---
### Please Note

>Continue reading only if you're interested in using Arc. Otherwise, this information may not be relevant to you.

Arc's Boost feature is pretty cool. As I wrote in the [last post](https://blog.motionbug.com/posts/dark-mode-with-arc/), we can change the colour of a site or even create our own custom dark mode. Moreover extends beyond basic browser functionality, allowing you to apply custom tweaks—akin to user scripts of the past, but seamlessly integrated into your browsing experience.

The capability to inject custom CSS and JavaScript means you can tailor any site to your liking. Whether it's implementing a dark mode, changing fonts, or even reorganizing layout elements, the power is in your hands.

For those who manage more then one Jamf Pro site, Arc can be especially useful.

Want to rename the **Pro** within the header of your Jamf Pro dashboard to reflect which Jamf Pro instance you are working on? Insert the following JavaScript code into an Arc Boost code feature, and replace 'New Text' with the name of your Jamf Pro instance what ever you want. Take it a step further and add some colour as well.

![simplerename](https://share.cleanshot.com/T135vBPZ+)

{{< gist motionbug ff9ac47e7581c1d45bc89978be713300 >}}
