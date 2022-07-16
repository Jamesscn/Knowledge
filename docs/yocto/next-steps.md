# Next Steps

## Customizing the Kernel

Now that you have built your custom Linux distribution, you can add or remove whatever you want. One of the most important parts of the build is the actual Linux kernel. You can control the kernel by running the menuconfig script, which will allow you to enable, disable or turn certain features into kernel modules. To run the menuconfig script, ensure you are in the build environment and run the following command:

    bitbake -c menuconfig virtual/kernel

After running this command, a .config file should be generated stating all of your customizations.

## Adding Packages and Layers

As stated earlier, you can visit the [OpenEmbedded Layers Index](https://layers.openembedded.org/layerindex/branch/master/layers/) to find more layers with packages you can install onto your system. Don't forget that the OpenEmbedded repository also has some layers which we haven't included yet!

Once you add a layer which contains the packages you want to install to the BBLAYERS variable, you can add the following line to your local.conf file, replacing the packages below with the names of the packages you want to install. Just make sure to conserve the space before and between each of the package names.

    IMAGE_INSTALL_append = " package1 package2 package3"

If you can't find a particular package, you can even create your own Yocto layer and create a recipe which will download and install that package. Just be aware that things can get a bit complicated with this method, so it is preferrable to use an existing layer if possible. While I have not found a good tutorial on how to create a layer, the following one explains very briefly how to create a layer and a recipe for a kernel module: [Yocto: Create a New Layer](https://yannik520.github.io/create_a_new_yocto_layer.html)