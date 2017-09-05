# The Vorteil Command-Line Interface
The Vorteil Command-Line Interface (vcli) provides all of the functionality you
need to run, build, or develop microservices and immutable infrastructure using
Sisa-Tech Pty Ltd's Vorteil kernel.

The lightweight Vorteil kernel is used to compile executable linux binaries into
bootable virtual machine disk images. Using a unikernel inspired approach, the
Vorteil kernel has virtually zero run-time overhead and boots up in a matter of
milliseconds.

# Commands

## apps
Download and manage Vorteil applications

#### build
Build a bootable virtual disk image from a Vorteil application

#### configure
Edit the configuration of an app (creates new version)

#### delete
Delete an application from the local repository

#### export
Copy a package from the local repository to a file

#### import
Import a package from a file into the local repository

### info
View information about an application's contents and configuration

### list
List the contents of the local repository

### pull
Download a Vorteil application from a remote repository

### push
Upload a Vorteil application to a remote repository

### run
Launch an application in a VM on a local hypervisor

### tag
Tag an application version

### unpack
Unpack the contents of an application package

### untag
Untag a tagged application version

## build
Build a bootable virtual disk image

## cloud
Upload apps directly to the cloud

## config
Change vcli settings and behaviour

## environments
Manage Vorteil environments

## kernels
Help about any command

## package
Manage Vorteil kernels

## prepare
Prepare a project with a Vorteil environment

## pull
Download a Vorteil application from a remote repository

## push
Upload a Vorteil application to a remote repository

## run
Run a Vorteil application

## unpack
Unpack the contents of an application package

## update
Update vcli's Vorteil kernel files

## vcfg
Configure Vorteil applications with 'vcfg' files

## version
Display vcli version information
