# Configuring Yocto

There are two main files which will be configured, the bblayers.conf file and the local.conf file. The bblayers.conf file is used to tell Yocto which layers will be used and where they are located, and the local.conf file is used for more general configuration, such as telling Yocto what type of system its building and where to store things.

## Layer Configuration

First, open the bblayers.conf file, which should have the following or similar contents:

    # POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
    # changes incompatibly
    POKY_BBLAYERS_CONF_VERSION = "2"

    BBPATH = "${TOPDIR}"
    BBFILES ?= ""

    BBLAYERS ?= " \
      /home/your_username/Documents/Yocto/poky/meta \
      /home/your_username/Documents/Yocto/poky/meta-poky \
      /home/your_username/Documents/Yocto/poky/meta-yocto-bsp \
      "

The part we are interested in is the **BBLAYERS** variable, which is a list of directories representing the layers to be installed. Currently, the meta, meta-poky and meta-yocto-bsp layers from Poky have been added. You now need to install some of the layers from the OpenEmbedded repository that was downloaded in the previous step because they serve as dependencies. Taking a look at the Yocto/meta-openembedded folder we can see there are many layers that can be added:

    $ ls ~/Documents/Yocto/meta-openembedded
    COPYING.MIT  meta-filesystems  meta-multimedia  meta-perl       meta-xfce
    README       meta-gnome        meta-networking  meta-python
    contrib      meta-initramfs    meta-oe          meta-webserver

The only necessary layer is the meta-oe layer, however if you want more features you can add the other folders as well to the BBLAYERS variable. You can paste the (absolute!) path to the meta-oe directory into our BBLAYERS variable as follows:

    BBLAYERS ?= " \
      /home/your_username/Documents/Yocto/poky/meta \
      /home/your_username/Documents/Yocto/poky/meta-poky \
      /home/your_username/Documents/Yocto/poky/meta-yocto-bsp \
      /home/your_username/Documents/Yocto/meta-openembedded/meta-oe \
      "

However you are not done yet, you still need to add the layer which contains the board support package for the Raspberry Pi 4, which is found in the Yocto/meta-raspberrypi folder:

    BBLAYERS ?= " \
      /home/your_username/Documents/Yocto/poky/meta \
      /home/your_username/Documents/Yocto/poky/meta-poky \
      /home/your_username/Documents/Yocto/poky/meta-yocto-bsp \
      /home/your_username/Documents/Yocto/meta-openembedded/meta-oe \
      /home/your_username/Documents/Yocto/meta-raspberrypi \
      "

With this, you have now told Yocto which layers you are going to use. You can confirm that these layers have been added correctly by running the following command. If no errors appear and you can see all the layers in the BBLAYERS variable then everything should be okay.

    bitbake-layers show-layers

## Editing local.conf

The next step is to edit the local.conf file. The main thing that needs to be changed here is the **MACHINE** variable, because this tells Yocto what type of architecture it is dealing with. What you need to do is to set the MACHINE variable the value *raspberrypi4*.

I recommend you place this line at the top of the file:

    MACHINE ?= "raspberrypi4"

Next, if you are going to build the distribution to an SD or micro-SD card, then you also need to add this line, which will generate an image which can be easily put on the SD card:

    IMAGE_FSTYPES = "rpi-sdimg"

That's just about everything you need to do in order to configure Yocto. You can play around with the settings in the local.conf file, just be careful not to break anything!