# Setting up the Development Environment

!!! info ""

    From now on, all the steps taken will assume that you are working inside your Linux machine, and that you have a working internet connection and sufficient hard drive space (at least 50 GB).

## Required Downloads

Before anything, you will have to install the following set of packages:

- build-essential
- chrpath
- diffstat
- gawk
- libncurses5-dev
- python3-distutils
- texinfo

If you are running one of the distributions below you can run the command that is shown. For other distributions these packages may vary or may already be installed, and will need to be installed through that distribution's package manager.

=== "Ubuntu"

    ```bash
    sudo apt install build-essential chrpath diffstat gawk libncurses5-dev python3-distutils texinfo
    ```

=== "Arch Linux"

    ```bash
    pacman -S chrpath diffstat gawk ncurses texinfo rpcsvc-proto
    ```

In order to start work on the distribution, you must first set up the foundations which you will use to build and compile everything. The first step is to create a folder where you will house your files. I decided to call my folder Yocto, and I put it in my Documents folder:

    └─ Documents/
        └─ Yocto/

Now that you have this folder, make sure to move into the Yocto directory. In my case, I would run the following command:

```bash
cd ~/Documents/Yocto
```

Before downloading anything, you must know which release of Yocto you will be using. At the time of this writing I will be doing all demonstrations with **kirkstone**, however you should consult the [releases page](https://wiki.yoctoproject.org/wiki/Releases) and choose the most recent Long Term Support release available.

In order to avoid having to build literally everything from scratch, we will be using Poky, which I like to think of as a blank template with a lot of useful tools. Poky is stored in a Git repository which has branches for every release, so you want to download the branch for **kirkstone** or whichever release you are going to use. This will be a recurring theme between Yocto related repositories. This can be done by running the following command:

    git clone -b kirkstone git://git.yoctoproject.org/poky

Next, you need to download the **meta-openembedded** layer, which again is a set of very helpful recipes for embedded systems. Just like with the Poky repository, you need to download the correct branch:

    git clone -b kirkstone git://git.openembedded.org/meta-openembedded

Finally, we need a layer which contains specific recipes which will allow our distribution to function on the Raspberry Pi 4, it is not enough to just have the Poky and OpenEmbedded layers for a specific architecture. This layer is what is known as a *board support package*. If you are building a distribution for a board other than the Raspberry Pi 4, there is likely a Git repository somewhere on the internet with the board support package for that board. You can download the relevant branch of the repository with the following command:

    git clone -b kirkstone git://git.yoctoproject.org/meta-raspberrypi

Your Yocto folder should now have three folders:

    └─ Documents/
        └─ Yocto/
            ├─ meta-openembedded/
            ├─ meta-raspberrypi/
            └─ poky/

## Optional Downloads

There are several other layers that can be downloaded to add more features to your Linux distribution. If this is your first time making a Yocto distribution, I would advise against adding these layers unless you know what you are doing or really require them because they will increase the amount of time it takes to build an image.

You can find a list of these layers in the [OpenEmbedded Layers Index](https://layers.openembedded.org/layerindex/branch/master/layers/).

## Entering the Build Environment

After everything has been downloaded you will need to enter the build environment which gives you access to a bunch of Poky commands and more importantly **bitbake**, which is the main build tool.

To start the build environment, you will have to navigate into the poky/ directory and run the following command:

    source oe-init-build-env

This will run the **oe-init-build-env** script, which will launch you straight into the build environment and put you inside a directory called build/, which will be the main space where you work on your distribution.

You can change the name of the build directory by adding the new name to the end of the previous command, however you should note that once the system has been built, you cannot change the name of the directory without rebuilding everything. I personally prefer the build directory to be called build/, therefore I left the previous command as-is.