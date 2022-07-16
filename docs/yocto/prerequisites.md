# Prerequisites

In order to follow this tutorial, you will need the following hardware and software components:

- **A machine running Linux**
    - While some distributions are not supported by the Yocto project for development, you can get away with using most of them anyways. The recommended distribution is Ubuntu, however I am using Arch Linux which is currently unsupported, yet everything still works fine.
    - You should be able to follow this tutorial if you are running Linux in a virtual machine, just make sure that you can read and write to the Micro-SD card used by the Raspberry Pi 4.
    - You should also ensure that you have a decent amount of memory, hard drive space and CPU power available, because creating images with Yocto requires a lot of resources and can take several hours to build. I would set aside at least 50 GB of space for this project.
- **Raspberry Pi 4** (Any model)
    - Make sure you have a way to power the Raspberry Pi and a way to connect to it. In my experience it is much easier to connect the Raspberry Pi to a screen, keyboard and mouse than to SSH into it.
- **Micro-SD card** (> 4 GB in size)
    - This is the storage card that will be used by the Raspberry Pi. You will need to overwrite the data on this card with your Linux distribution in order to run it on the Raspberry Pi.
- **Micro-SD to SD card adapter**
    - Unless your PC comes with a Micro-SD card reader, you will need this adapter in order to read and write to the Micro-SD card. Make sure your computer has an SD card reader, otherwise you will need another type of adapter.