---
layout: post
title:  "Installing AVR GCC on OS X"
date:   2014-02-08 21:27:00
categories: avr
---

The `avr-gcc` compiler can be installed on OS X via Home Brew. Currently it's not part of any official formula, but it can be install easily enough using taps.

On OS X Mavericks (10.9.1) I simply:

    brew tap larsimmisch/avr
    brew install avr-libc
    
It took my Mac a little bit to compile all the build tools, but everything worked out fine.
