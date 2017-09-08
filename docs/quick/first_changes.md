# Building your own Vorteil App

Let’s do something a bit more interesting. There’s nothing special about the application we’re running inside the helloworld package: it simply needs to be a binary compiled for linux. In fact, if you unpack this package and run the helloworld binary from the terminal you’d see exactly the same behaviour as you just saw on the virtual machine (if you’re using Linux).

VCLI makes it easy to build your own Vorteil App. To keep things simple, we'll demonstrate this by just making a small change to the runtime environment provided by Vorteil to the helloworld application so that we don’t have to worry about changing any code or cross-compiling for Linux if you’re on Windows or Mac.

## Unpacking the helloworld package

```bash
vcli unpack
```

VCLI's unpack command will extract all of the files contained within the helloworld.vorteil package to a new directory called "helloworld", making them available for us to modify. Inside you should see the following:

- **helloworld**: the Linux binary that Vorteil will run
- **helloworld.files**: a directory containing all of the files that will be built onto the filesystem of the virtual machine disk
- **helloworld.vcfg**: a YAML configuration file containing information VCLI uses when building the virtual machine disk
- **vorteil.png**: an icon for the package

## Changing the runtime environment

The helloworld program was designed to set the background of the “Welcome to Vorteil” webpage to the colour stored in the BACKGROUND environment variable. Let's change the colour from white to black.

Open “helloworld/helloworld.vcfg” in your preferred text editor. Inside you should see a section containing the following:

```yaml
env:
  vars:
    BACKGROUND: "0xFFFFFF"
```

Replace it with the following:

```yaml
env:
  vars:
    BACKGROUND: "0x000000"
```

Save and close the configuration file.

## Test run non-packaged files

```bash
vcli run helloworld
```

VCLI isn’t just capable of running packages, it can also assemble the information it needs from unpackaged files. Use the “vcli run” command like you did before, but this time make sure to target the unpacked files, not the helloworld package from before. Try running “vcli run helloworld”, which tells VCLI to use the files within the “helloworld” directory. Once your virtual machine is up and running, check if the application is working by visiting [http://localhost:8888/](http://localhost:8888/).

When you're finished, use 'CTRL+C' in the terminal running VCLI, or close the virtual machine manually to close the application. See the [FAQ](../debug/faq.md).

Now that you’ve seen your changes working locally, it’s time to get it online and on The Internet. We’ve provided an online platform just for Vorteil applications at go-vorteil.io for this very purpose.

## Package your modified application

```bash
vcli package helloworld --icon helloworld/vorteil.png
```

Before we can upload or distribute our file to we’ll need to re-package it with our changes. Use “vcli package helloworld” to generate a new package from the modified files in your “helloworld” directory. This will overwrite the original package “helloworld.vorteil” unless you renamed it earlier.
