---
layout: post
title:  "Hacking Bluetooth LE"
date:   2014-02-10 22:18:00
categories: avr
---

Inspired by recently reading [an article](http://hackaday.com/2013/09/21/sending-data-over-bluetooth-low-energy-with-a-cheap-nrf24l01-module/) on Hack a Day about emulating Bluetooth LE with a cheap nRF24L01+ module, I decided to take the plung and order some off eBay. I ended up spending $11.96 for ten units with shipping included, so about $1.20 per unit. More than enough extras to have some fun :-)

My initial thoughts were to use Dmitry's [example](http://dmitry.gr/index.php?r=05.Projects&proj=15&proj=11.%20Bluetooth%20LE%20fakery) for bit-banging BTLE, but adapt it to run on an ATMega328-PU. This turned out to be a little more difficult than I expected mainly due to (I suspect) differences between the compiler Dmitry was using and AVR GCC. For example, Dmitry's code makes use of the `cbi` and `abi` functions. I'm not familiar with these, and a few searches revealed that they've been missing (deprecated then removed actually) from AVR GCC for some time. Not fully understanding the purpose of those functions either I was handicapped in my porting efforts.

I eventually found [a port](https://github.com/sandeepmistry/arduino-nRF24L01-BLE) of this sample to Arduino and from that I was able to infer what should be done. Eventually, I ended up with this:

<script src="https://gist.github.com/jwhitehorn/8929306.js"></script>

Unfortunately this doesn't seem to do anything. At least, not according to [iStumbler](http://www.istumbler.net) - running their Bluetooth scanner didn't reveal any signs that my little AVR was broadcasting.

This was about as far as I was able to make it over the weekend, so I don't yet know what the problem is. I suspect that either I'm using iStumbler wrong, or there's something wrong with the way I ported the SPI implementation. 

Either way, that's something I'll have to dig into later.
