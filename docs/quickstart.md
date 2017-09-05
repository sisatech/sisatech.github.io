# Quick Start Guide

Getting started with Vorteil is easy. You only need to do these three simple steps.

## Step 1 - Install VCLI

VCLI is the Vorteil Command-Line Interface. It is the only tool you’ll need to work with Vorteil.

[VCLI Installation Guide](vcli.md)

### Linux

__Step 1 : Install a hypervisor__

If you don't already have a hypervisor installed, the following command will install KVM:

		sudo apt-get install qemu-kvm
Other supported hypervisors on Linux are VMware Workstation, VMware Workstation Player, and Oracle VirtualBox

***NOTE (Mac / Windows):***
*VCLI will automatically check most default paths for VirtualBox / VMware installations.*
*If you specified a custom installation path, please ensure that it has been added to your PATH.*

###  Mac OS X

__Step 1: Install a hypervisor__

Download and install your preferred hypervisor software:

[VirtualBox](https://www.virtualbox.org/)

[VMware Fusion](https://www.vmware.com/)

### Windows

__Step 1: Install a hypervisor__

Download and install your preferred hypervisor software:

[VirtualBox](https://www.virtualbox.org/)

[VMware Workstation or Workstation Player](https://www.vmware.com/)

Make sure you add your respective [hypervisor location to the PATH](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/).


If you’re using Bash, command auto-completion will be enabled the next time you log onto your computer.


## Step 2 - Get a Vorteil App

You’ll need a Vorteil App to run. Anyone can build their own Vorteil App, but for now let’s grab one from the official online repository. We will use Sisa-Tech’s HelloWorld application package for this quickstart demo.

		vcli apps pull sisatech/helloworld

This command downloads the package into VCLI’s local repository for easy access, organization, and version control.

## Step 3 - Compile and Run the App

Now that we have an application package stored in our local repository we need to build and run it as a virtual machine. The HelloWorld package comes with all of the information VCLI needs to make it run, so you don’t need to do anything except run it.

		vcli apps run sisatech/helloworld

Congratulations! You should now be able to visit the HelloWorld webpage hosted on a virtual machine on your own computer by visiting http://localhost:8080/.
