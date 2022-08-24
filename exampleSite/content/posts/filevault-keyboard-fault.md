---
title: Jamf Connect, Filevault and the USA Keyboard
date: 2022-08-05
description: 'Did you ever find'
image: images/mac-kb.png
---

## "Sorry my password doesn't seem to work!"

I recently ran into an issue where my customer was having a problem with the FileVault login window and entering their password. After a bit of trouble shooting we figured it out. There was a pretty strong password policy in place and being a UK organisation the keyboard was set to British English but the problem was the keyboard within the FileVault login windows was American English. Special characters like the @ or # are not in the same spot.

### Where does FileVault store the keyboard prefrences

Where does the FileVault login window store the keyboard settings? After some conversations with some really smart people 

### Finding the right IDs for each keyboard

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


