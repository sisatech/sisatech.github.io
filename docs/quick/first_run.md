# Running your first Vorteil App

!> Follow the Installation instructions for your operating system first.

VCLI (Vorteil Command-Line Interface) is the primary tool you'll need to work with Vorteil.
Let's dive in and see how easy it is to start using VCLI.
To keep things simple, we'll download a simple Hello World application from Sisa-Tech's online repository.

## Get a Vorteil App

```bash
vcli pull sisatech/helloworld
```

This command connects to Sisa-Tech's online Vorteil Apps Marketplace and downloads the pre-prepared helloworld package into your current directory. Vorteil Packages can be identified by their ".vorteil" file extension, so after you run this command you should see helloworld.vorteil in your current directory.

## Run a Vorteil App in a Virtual Machine

```bash
vcli run
```

Vorteil packages contain everything VCLI needs to build and start a Virtual Machine running an application on the Vorteil Kernel. The helloworld application we downloaded is designed to run a simple "Welcome to Vorteil" webpage listening on port 8888. Once your virtual machine is up and running, check if the application is working by visiting [localhost:8888](localhost:8888).

![Hello World](/quick/white-background-helloworld.png)

When you're finished, use 'CTRL+C' in the terminal running VCLI, or close the virtual machine manually to close the application. See the [FAQ](../debug/faq.md).
