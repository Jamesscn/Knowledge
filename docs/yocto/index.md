# Making a Linux Distribution for Raspberry Pi

This tutorial will cover how to create an embedded Linux distribution with the **bare minimum** installed using the Yocto Project for the Raspberry Pi 4. While there are other tutorials out there, I have found them to be vague, and some of them require you to download special tools in order to actually make the distribution.

This tutorial focuses on the Raspberry Pi 4 because it is one of the more commercially available embedded boards capable of running Linux (at least at the time of this writing). That being said, most of the information presented can be extrapolated to build a distribution for another board given that a *board support package* for it exists.

## What is a Linux Distribution?

By Linux distribution, I am referring to the combination of the Linux kernel (the core of Linux, which allows programs to interact with the system's hardware) and a set of packages, which are programs which run upon the Linux kernel such as bash, gcc and python.

## Why make a Linux Distribution?

The main reasons for building a Linux distribution are to either to gain a better understanding of how Linux works, or to port Linux to a customly designed embedded device with strict requirements which you can control.

Apart from these reasons, given that there are many distributions with extremely strong support that can be installed on just about any system, there is little need to build a distribution. Nevertheless, I still find the idea of creating a Linux distribution fun, therefore I have decided to create this tutorial.

## Other Resources

If you are looking for other material to complement this tutorial, or are simply looking for something else, these resources may be good for you.

I thoroughly recommend Digikey's series on building an embedded Linux distribution, as it covers the material presented in this tutorial and more: [Introduction to Embedded Linux](https://www.youtube.com/playlist?list=PLEBQazB0HUyTpoJoZecRK6PpDG31Y7RPB). It is different to this tutorial in that a STM32MP157D-DK1 board is used instead of the Raspberry Pi 4, which is slightly harder to acquire.

I also heavily recommend taking a look at Bootlin's slides on Yocto, as they are very informative and explain Yocto in much greater detail: [Yocto Project and OpenEmbedded system development training](https://bootlin.com/doc/training/yocto/yocto-slides.pdf)