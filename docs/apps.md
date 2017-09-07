# apps
Download or manage a local repository of Vorteil application packages. vcli
maintains a database of Vorteil applications that have been downloaded or
imported in order to provide helpful version control, data deduplication, and
a standardized location for publically distributed Vorteil applications.

Applications stored within the local repository have a name and a reference ID.
The name can include parent directories for organizational purposes. For
example, a "Hello, World!" application provided by Sisa-Tech Pty Ltd would
commonly be named "sisatech/helloworld". The reference ID is used for version
control when multiple versions of the same application exist within the
repository.

Other vcli commands that can accept a Vorteil package as an argument or flag can
access applications within the local repository by prefixing the location with
"apps:", like "apps:sisatech/helloworld". If a specific version of the app is
required, the location can have an optional suffix containing the reference ID,
like so: "apps:sisatech/helloworld:a9c9c21a0339".


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

#### info
View information about an application's contents and configuration

#### list
List the contents of the local repository

#### pull
Download a Vorteil application from a remote repository

#### push
Upload a Vorteil application to a remote repository

#### run
Launch an application in a VM on a local hypervisor

#### tag
Tag an application version

#### unpack
Unpack the contents of an application package

#### untag
Untag a tagged application version

<!-- ## build
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
Display vcli version information -->
