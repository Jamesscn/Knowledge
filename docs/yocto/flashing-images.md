# Flashing the Image to the Micro-SD Card

Now that you have created your image, the next step is to burn it onto the Micro-SD card. Make sure to connect it to the Micro-SD to SD adapter and plug it into your computer. Once you have done this should be able to see the card.

Be certain that you have moved any important information off of the Micro-SD card before proceeding, because we will be overwriting the data on the card with the image.

The next step is to determine where your device is loaded in the /dev/ folder. This can be done in several ways, and I recommend using a graphical program such as GParted to verify that you are looking at the correct device. The easiest way to do this though is to run the `lsblk` command before plugging in the Micro-SD card and after doing so. Here, I am showing the output of the command before plugging in the Micro-SD card:

    $ lsblk
    NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
    sda           8:0    0 931.5G  0 disk 
    ├─sda1        8:1    0 286.2G  0 part /
    ├─sda2        8:2    0  16.1G  0 part [SWAP]
    └─sda3        8:3    0 629.3G  0 part 
    nvme0n1     259:0    0 238.5G  0 disk 
    ├─nvme0n1p1 259:1    0   250M  0 part 
    ├─nvme0n1p2 259:2    0   128M  0 part 
    ├─nvme0n1p3 259:3    0 218.8G  0 part 
    ├─nvme0n1p4 259:4    0   990M  0 part 
    ├─nvme0n1p5 259:5    0    17G  0 part 
    └─nvme0n1p6 259:6    0   1.4G  0 part 

And after plugging it in this is what is shown:

    $ lsblk
    NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
    sda           8:0    0 931.5G  0 disk 
    ├─sda1        8:1    0 286.2G  0 part /
    ├─sda2        8:2    0  16.1G  0 part [SWAP]
    └─sda3        8:3    0 629.3G  0 part 
    sdb           8:16   1    58G  0 disk 
    ├─sdb1        8:17   1    40M  0 part 
    └─sdb2        8:18   1   144M  0 part 
    nvme0n1     259:0    0 238.5G  0 disk 
    ├─nvme0n1p1 259:1    0   250M  0 part 
    ├─nvme0n1p2 259:2    0   128M  0 part 
    ├─nvme0n1p3 259:3    0 218.8G  0 part 
    ├─nvme0n1p4 259:4    0   990M  0 part 
    ├─nvme0n1p5 259:5    0    17G  0 part 
    └─nvme0n1p6 259:6    0   1.4G  0 part

You can see that a new device, **sdb**, has now appeared with a size of 58 GB. This is close to the 64 GB of capacity my Micro-SD card is supposed to hold, therefore I am quite certain that my Micro-SD card is mounted at /dev/sdb.

However it is very important that you run these commands on your machine and verify where your Micro-SD card is mounted, because this can change *even on the same computer*. If you overwrite /dev/sdb without verifying that your Micro-SD card is there, it may lead to a **catastrophic loss of data**.

Now that you have determined where to write the data to, you can proceed to use the `dd` command to start writing your image to the Micro-SD card. In the next steps I will be using /dev/sdX as the place where the Micro-SD card is mounted at. Remember that you have to change this to the place where you have your Micro-SD card.

!!! danger "Warning!"
    The `dd` command is extremely dangerous and can **permanently delete your hard drive**. Make sure you are overwriting the **correct** device.

In order to write the image to the Micro-SD card, run the following commands from the build/ directory, replacing all instances of **/dev/sdX**.

    sudo umount /dev/sdX
    sudo dd if=tmp/deploy/images/raspberrypi4/core-image-base-raspberrypi4.rpi-sdimg of=/dev/sdX
    sync
    sudo umount /dev/sdX

After this, your Micro-SD card should have two partitions, one with a bunch of .dat and .elf files and another with the actual filesystem of your image. You should now be able to connect your Micro-SD card to the Raspberry Pi and run your custom Linux distribution.