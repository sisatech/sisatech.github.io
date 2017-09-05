## build
Build a bootable virtual disk image.
The standard disk format 'vmdk' is a "sparse extent" Virtual Machine Disk
(.vmdk) file. The sparse vmdk can be imported by most local hypervisors such as
QEMU and VirtualBox. Alternative formats can be specified with the 'format'
flag and include: raw, vmdk, stream-optimized-vmdk, ova, vhd, gcp.

	raw:
		a simple and uncompressed disk image format
	stream-optimized-vmdk:
		alternative compressed vmdk format sometimes used by vmware
	ova:
		VMware's preferred format for use with vSphere and ESXi
	vhd:
		Microsoft's preferred format for use with Azure
	gcp:
		Google's preferred format for use with Google Cloud Platform


#### args
Specify binary args

#### argv0
Specify name and path for the binary on the VM

#### config
Use named config files

#### cpus
Number of virtual CPUs

#### debug, d
Build with debug kernel

#### disk-size
Size of the filesystem partition in MiB

#### file-system
Filesystem implementation

#### files
Merge directories into filesystem

#### format
Specify a virtual disk format (default "vmdk")

#### hostname
Specify VM hostname

#### kernel
Specify Vorteil kernel

#### memory
Virtual RAM in MiB

#### nic
Define network cards' settings

#### output, o
Write disk to named output file

#### port
Add port rules

#### redirect
Add filesystem redirects

#### var
Set environment variables

#### verbose, v
Verbose output

<!-- ## cloud
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
Display vcli version information -->
