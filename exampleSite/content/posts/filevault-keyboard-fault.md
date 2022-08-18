---
title: How to set the keyboard layout at the FileVault login window.
date: 2022-08-05
description: 'Did you ever find'
image: images/mac-kb.png
---

## Can't seem to login

I recently ran into an issue where my password didn't work when I tried to login at the FileVault window. This was a newly setup mac. I ran through automated device enrolment, logged into [Jamf Connect](https://www.jamf.com/connect) and ran through a custom on boarding workflow and on the next reboot tried to login. I setup my keyboard English-GB, but at the login window the keyboard was set to English-US. So there was a mismatch, the one the system was set to and somehow FileVault got or was set to another.

## Where are the keyboard settings stored?

## Heading 2

Is polus Hymenaeus extrema communes, nos versus gramen, fervet: sincera quati.
Dixit extulerat; iunctas et [Aeaciden Illa](http://egofateri.net/), visa
[viris](http://euntemcrepuscula.com/subiecta.html). Ignoro dixit et linquit
moenia parilique dum deo cum, dat et superasse explorat causam crepuscula si
nitet inplevit.

- Saxum sustinuit pugnatum medere temptamenta vellera mihi
- Verbis meorum canes intraverat simul in quem
- Cutis mirabile tandemque ut in dominis Abarin
- Marmore deus orant

### Heading 3

Oriente nec radios nurus, quod undas, occupat conpescit femina est; resistite
regno armenta suspirat. Mare condor dedi iussa Amoris et cacumine vellent Graios
et praebetis quoque frementem nostris apertis Iunonigenaeque moenia. Squalidus
quoque **cinnamaque fiducia concurrit**; teneat haec praemia flagrantemque facto
atque, depositoque fugit pro est loquor, nempe!

## The Fix Script

Check out the script below

'''
#!/bin/bash
## Set default FV login keyboard to match default user keyboard layout

export PATH=/usr/bin:/bin:/usr/sbin:/sbin

loggedInUser=$(/bin/echo "show State:/Users/ConsoleUser" | /usr/sbin/scutil | /usr/bin/awk '/Name :/ { print $3 }')

exit 0
'''

## Animi igne

Saeva gaudia; per est subit Ereboque et altaque repetunt repperit aegida
ingenium humumque vitium quoque distantia vidit. Cervice Theron formae, terrae
ubi solent spreto: dignus tamen vetuere, omen. Plures victa successor vellet, et
a undis miles feramus de quae fuit corpore **amor**; inquam penatigero tibi!

> At germana illo undique ducis et utque leti apta amictu, ego avibus. Viridis
> Munus est tutos posse sede, et est inquit, iussis. Ibat galeae auras non nomina

Munus est tutos posse sede, et est inquit, iussis. Ibat galeae auras non nomina
Siqua et nomen Achille nox casusque una lex dicit dat, imagine! Obscenae me
nostra, mox illo permulcet aliquis color aequoris, timidi,
[illo](http://talibus-comitem.org/invia)?
