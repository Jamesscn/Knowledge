# About the Yocto Project

## What exactly is the Yocto Project?

Yocto is a tool used to create Linux distributions for embedded devices with ease. In the past, making a Linux distribution was an incredibly hard feat for several reasons, such as the fact that a considerably large amount of work had to be done to build the distribution and support it across different architectures, and the fact that programmers needed a ridiculously large amount of knowledge to understand how every small component works.

However, with Yocto anyone can create a Linux distribution from their home computer or laptop by downloading the necessary components and configuring them in a matter of hours. One of the advantages of Yocto is that if you build a distribution and decide to make a small change, it only needs to compile that change because it keeps its progress, saving you a lot of time.

Yocto uses *layers* and *recipes* in order to create a Linux distribution. A *recipe* is essentially a script which tells Yocto how to install a package or program on the system, telling it where to download the package, where to put it, how to compile it and any other necessary steps. A *layer* is a group of recipes, and each layer usually holds recipes related to a specific purpose or functionality. For example, a common layer is the meta-networking layer from the OpenEmbedded core. This layer holds recipes for many networking related packages.

Yocto is build up of three core components that will be mentioned in the next steps. These three components are the following:

- **Poky**: It is a reference system or a blank template with a bunch of useful tools.
- **OpenEmbedded core**: A set of layers containing basic packages which are common in most Linux distributions.
- **Bitbake**: A powerful script which builds everything, from individual packages up to the entire distribution.

Together, these three components make up the Yocto project.