---
title: Jamf Connect, Filevault and the USA Keyboard
date: 2022-08-05
description: 'Did you ever find'
image: images/mac-kb.png
---

# "My password doesn't seem to work!"

I recently ran into an issue where my customer was having a problem with the FileVault login window and entering their password. After a bit of trouble shooting we figured it out. There was a pretty strong password policy in place and being a UK organisation the keyboard was set to British English but at the FileVault login windows the keyboard was American English. Big problem as the special characters like the "**@**" or "**#**" are not in the same spot.

### Where does FileVault store the keyboard prefrences

To fix this issue we needed to find out Where does the FileVault login window stores the keyboard settings? After some conversations with some really smart people we found that they keyboard is stored within the **nvram** on the mac.

A simple command `sudo nvram prev-lang:kbd="en_GB:2"` sets the keyboard to British within the FV window. So we could just create a simple policy that ran this command and fix all UK keyboards. That would work for the UK, but what about the rest of the people around the world.

### Finding the right IDs for each keyboard

Thanks to the **macadmins** slack 
https://macadmins.slack.com/archives/CCWGRUFKN/p1643833928628799?thread_ts=1643822101.694119&cid=CCWGRUFKN

https://raw.githubusercontent.com/acidanthera/OpenCorePkg/ef2db45050c4aed6aa2e93d7c00df45706ab4e13/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt


## The Fix

{{< gist motionbug f0820d062a7dcbaf5f18efc39d114f18 >}}

Check out the script below

```
#!/bin/bash
## Set default FV login keyboard to match default user keyboard layout

export PATH=/usr/bin:/bin:/usr/sbin:/sbin

loggedInUser=$(/bin/echo "show State:/Users/ConsoleUser" | /usr/sbin/scutil | /usr/bin/awk '/Name :/ { print $3 }')

exit 0
```


