---
title: Jamf Connect, Filevault and the USA Keyboard
date: 2022-08-05
description: 'Filevault keyboard is set to USA ABC and your password does not work. I will walk you through on what you need to do to change it to your local language'
image: images/mac-kb.jpg
tags: ['Jamfconnect', 'Filevault']
---

## "My password doesn't seem to work!"

I recently ran into an issue where my customer was having a problem with the FileVault login window and entering their password. After a bit of troubleshooting, we figured it out. There was a pretty strong password policy in place and being a UK organisation the keyboard was set to British English, but at the FileVault login windows the keyboard was American English. Big problem as the special characters like the "**@**" or "**#**" are not in the same spot.

### Where does FileVault store the keyboard preferences

Fixing this issue, we needed to find out where does the FileVault login window store the keyboard settings? After some conversations with some really smart people [@scriptingosx](https://twitter.com/scriptingosx) we found that they keyboard is stored within the **NVRAM** on the mac.

A simple command `sudo nvram prev-lang:kbd="en_GB:2"` sets the keyboard to British within the FV window. We could just create a simple policy that ran this command and fix all UK keyboards. That would work for the UK, but what about the rest of the people around the world?

### Finding the right IDs for each keyboard

Thanks to the **macadmins** slack, there was a [thread discussing](https://macadmins.slack.com/archives/CCWGRUFKN/p1643833928628799?thread_ts=1643822101.694119&cid=CCWGRUFKN) the `nvram` command, and someone found a list that had all the keyboard IDs within an Apple dat file. The OpenCore projects has [a list with all the keyboard layout IDs](https://raw.githubusercontent.com/acidanthera/OpenCorePkg/ef2db45050c4aed6aa2e93d7c00df45706ab4e13/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt)

### How to fix

First we need to get the current user's default keyboard reading the ID from `com.apple.HIToolbox.plist` and once we have that we can look up the keyboard from the OpenCore [list](https://raw.githubusercontent.com/acidanthera/OpenCorePkg/ef2db45050c4aed6aa2e93d7c00df45706ab4e13/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt).

### Final script

The final script will find the keyboard, lookup the name/ID and run the `nvram` command. Easy to add this to a policy during the onboarding process to fix the keyboard on within FV login window.

{{< gist motionbug f0820d062a7dcbaf5f18efc39d114f18 >}}

Hope this helps, it helped the rollout that I was working on.
