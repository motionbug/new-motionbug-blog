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

```shell
#!/bin/bash

export PATH=/usr/bin:/bin:/usr/sbin:/sbin
### set default FV login keyboard to match default user keyboard layout

#Variables
globalprefs=$(defaults read .globalpreferences.plist)

IFS=','
Kbdcodes='
|30778| cs - Czech-QWERTY,
|30776| cs - Czech,
|30764| et - Estonian,
|30767| hu - Hungarian-QWERTY,
|30763| hu - Hungarian,
|30765| lv - Latvian,
|30761| lt - Lithuanian,
|30788| pl - Polish Pro,
|30762| pl - Polish,
|30777| sk - Slovak,
|30779| sk - Slovak-QWERTY,
|19529| bg - Bulgarian - Phonetic,
|19528| bg - Bulgarian,
|19517| be - Byelorussian,
|19523| mk - Macedonian,
|19457| ru - Russian - Phonetic,
|19456| ru - Russian,
|19458| ru - RussianWin,
|19521| sr-Cyrl - Serbian,
|195138| uk - Ukrainian-PC,
|19518| uk - Ukrainian,
|12825| en - Colemak,
|16302| en - Dvorak - Left,
|16303| en - Dvorak - Right,
|16300| en - Dvorak,
|16301| en - DVORAK - QWERTY CMD,
|16384| ja - KANA,
|251| fr - ABC-AZERTY,
|253| de - ABC-QWERTZ,
|252| en - ABC,
|15| en_AU - Australian,
|92| de_AT - Austrian,
|6| nl_BE - Belgian,
|128| pt_BR - Brazilian-ABNT2,
|72| pt_BR - Brazilian - Pro,
|71| pt_BR - Brazilian,
|250| en_GB - British-PC,
|2| en_GB - British,
|80| fr_CA - Canadian - CSA,
|29| en_CA - Canadian,
|9| da - Danish,
|26| nl - Dutch,
|17| fi - Finnish,
|60| fr - French-PC,
|1111| fr - French - numerical,
|1| fr - French,
|3| de - German,
|50| en - Irish,
|223| it - Italian - Pro,
|4| it - Italian,
|12| nb - Norwegian,
|10| pt_PT - Portuguese,
|87| es - Spanish - ISO,
|8| es - Spanish,
|7| sv - Swedish - Pro,
|224| sv - Swedish,
|18| fr_CH - Swiss French,
|19| de_CH - Swiss German,
|88| to - Tongan,
|0| en_US - U.S,
|15000| en_US - USInternational-PC,
|-17409| ko - 2SetHangul,
|-2902| fa - Afghan Dari,
|-2904| ps - Afghan Pashto,
|-2903| uz-Arab - Afghan Uzbek,
|-20000| ta - Anjal,
|-17940| ar - Arabic-AZERTY,
|-17923| ar - Arabic-North_Africa,
|-18000| ar - Arabic-QWERTY,
|-17920| ar - Arabic,
|-17921| ar - Arabic PC,
|-28161| hy - Armenian-HM QWERTY,
|-28164| hy - Armenian-Western QWERTY,
|-49| az-Latn - Azeri,
|-22529| bn - Bangla-QWERTY,
|-22528| bn - Bangla,
|-16899| zh-Hant - CangjieKeyboard,
|-26112| chr - Cherokee-Nation,
|-26113| chr - Cherokee-QWERTY,
|-68| hr - Croatian,
|-69| hr - Croatian-PC,
|-20481| hi - Devanagari-QWERTY,
|-20480| hi - Devanagari,
|-47| fo - Faroese,
|-17| fi - Finnish Extended,
|-18| fi - FinnishSami-PC,
|-27650| ka - Georgian-QWERTY,
|-18944| el - Greek,
|-18945| el - Greek Polytonic,
|-21505| gu - Gujarati-QWERTY,
|-21504| gu - Gujarati,
|-20993| pa - Gurmukhi-QWERTY,
|-20992| pa - Gurmukhi,
|-50| haw - Hawaiian,
|-18500| he - Hebrew-QWERTY,
|-18432| he - Hebrew,
|-18433| he - Hebrew-PC,
|-21| is - Icelandic,
|-30604| iu - Inuktitut-Nunavut,
|-30602| iu - Inuktitut-Nutaaq,
|-30600| iu - Inuktitut-QWERTY,
|-30603| iu - Inuttitut Nunavik,
|-500| ga - Irish Extended,
|-19000| ms-Arab - Jawi-QWERTY,
|-24065| kn - Kannada-QWERTY,
|-24064| kn - Kannada,
|-19501| kk - Kazakh,
|-26114| km - Khmer,
|-17926| ckb - Kurdish-Sorani,
|-24577| ml - Malayalam-QWERTY,
|-24576| ml - Malayalam,
|-501| mt - Maltese,
|-51| mi - Maori,
|-25601| my - Myanmar-QWERTY,
|-20484| ne - Nepali,
|-1200| se - Northern Sami,
|-12| nb - Norwegian Extended,
|-13| nb - NorwegianSami-PC,
|-22017| or - Oriya-QWERTY,
|-22016| or - Oriya,
|-1959| fa - Persian-QWERTY,
|-17960| fa - Persian,
|-2901| fa - Persian-ISIRI 2901,
|-38| ro - Romanian-Standard,
|-39| ro - Romanian,
|-1201| se - Sami-PC,
|-19521| sr-Latn - Serbian-Latin,
|-25089| si - Sinhala-QWERTY,
|-25088| si - Sinhala,
|-66| sl - Slovenian,
|-15| sv - SwedishSami-PC,
|-20001| ta - Tamil99,
|-23553| te - Telugu-QWERTY,
|-23552| te - Telugu,
|-26626| th - Thai-PattaChote,
|-26624| th - Thai,
|-26628| bo - TibetanOtaniUS,
|-26625| bo - Tibetan-QWERTY,
|-2398| bo - Tibetan-Wylie,
|-36| tr - Turkish-QWERTY-PC,
|-35| tr - Turkish-QWERTY,
|-23| tr - Turkish-Standard,
|-24| tr - Turkish,
|-2| en - US Extended,
|-1| <null> - Unicode Hex Input,
|-17925| ur - Urdu,
|-27000| ug - Uyghur,
|-31232| vi - Vietnamese,
|-790| cy - Welsh,
|-16900| zh-Hant - Zhuyin
'

loggedInUser=$(/bin/echo "show State:/Users/ConsoleUser" | /usr/sbin/scutil | /usr/bin/awk '/Name :/ { print $3 }')

#get current default keyboard ID number
KybdID=$(defaults read /Users/${loggedInUser}/Library/Preferences/com.apple.HIToolbox AppleEnabledInputSources | grep "KeyboardLayout ID" | awk -F '=' '{ print $2 }' | awk -F ';' '{ print $1 }' | awk -F ' ' '{ print $1 }')

#get the country code and create final value to apply
fullcode=$(echo $Kbdcodes | grep -w "|${KybdID}|")
countryCode=$(echo $fullcode | awk -F ' ' '{ print $2 }')
setcode="${countryCode}:${KybdID}"

#Set FV default Keyboard
nvram prev-lang:kbd="${setcode}"
exit 0
```

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
