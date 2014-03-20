---
layout: post
title:  "初试awesome"
date:   2014-03-18
comments: true
categories: 
tags: ["awesome"]
---

这些天右手腕有些酸痛，时不时的酸痛让人心烦，开始也没多想，后来上网搜索时才知道原来是鼠标手。

俺不禁疑惑，用电脑也接近四五年了，咋现在才出现鼠标手捏？我把注意力集中在那刚服役没多久的鼠标身上。这鼠标是我3块钱包邮在淘宝买的，一直放在角落里吃灰，直到前些天我把上个鼠标送给我妹妹。鼠标可能只是手疼的原因之一，根本性的解决方案是少用鼠标，多活动。

so，学习使用awesome便提上了日程。

安装与配置
----------

安装

	sudo pacman -S awesome

因为还不是太熟悉awesome的使用，所以开始只在startx中使用awesome，DM中仍使用xfce4，这样两个能同时用。

把下面添加到`~/.xinitrc`中

	exec awesome

然后在终端中运行`startx`，启动成功～

快捷键
------

Mod4	Super键即Windows键
C		Control
S		Shift
A		Alt

刚学会的快捷键

* Mod4 + r		Run prompt
* Mod4 + x		Run Lua code prompt
* Mod4 + Enter	Spawn terminal emulator
* Mod4 + w		Open main menu

* Mod4 + m		Maximize client
* Mod4 + n		Minimize client
* Mod4 + f		Set client fullscreen
* Mod4 + S + c	Kill focused client
* Mod4 + t		Set client on-top

* Mod4 + j		Focus next client
* Mod4 + k		Focus previous client
* Mod4 + Left	View previous tag
* Mod4 + Right	View next tag
* Mod4 + 1-9	Switch to tag 1-9

* Mod4 + h		Decrease master width factor by 5%
* Mod4 + l		Increase master width factor by 5%

* Mod4 + Space	Switch to next layout

* Mod4 + S + r  Quit awesome

开始先学那么多吧，再多就记不住了。
