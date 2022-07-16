# Building an Image with Bitbake 

!!! warning "Note"
    Building a Yocto distribution is very resource heavy and usually takes several hours to complete depending on your computer's processing power and your network connection, even while doing a minimal build. Furthermore, builds can occupy anywhere from 50 to 200 GB of space on your hard drive, so make sure you are ready for this before you start the build.

You are just about ready to start building your Linux distribution. There are several different *targets* or builds that can be done, ranging from minimal builds to toolchain-specific builds and more. In our case we are only currently interested in a minimal build, so we will run the following command. The command will likely take several hours to run and does not require you to answer any prompts, so I recommend you leave it running and ocasionally check back every now and then:

    bitbake core-image-minimal

Once the build has completed you should be able to see a bunch of files in the build/tmp/deploy/images/ folder. This folder holds your generated image. The image we are interested in is the one named `core-image-base-raspberrypi4.rpi-sdimg`.