---
title: Best not to use the serial number as a computer name.
date: 2022-08-05
description: 'Update your naming convention, don't use serial numbers to name your computers. Use something else'
image: images/about-mac.jpg
---

## Can't seem to login

I recently ran into an issue where my password didn't work when I tried to login at the FileVault window. This was a newly setup mac. I ran through automated device enrolment, logged into [Jamf Connect](https://www.jamf.com/connect) and ran through a custom on boarding workflow and on the next reboot tried to login. I setup my keyboard English-GB, but at the login window the keyboard was set to English-US. So there was a mismatch, the one the system was set to and somehow FileVault got or was set to another.