# What is vorteil.io?

The idea of vorteil is to run your applications in a virtual machine with the following concepts in mind:

1. Immutable Infrastructure

The vorteil command line interface (VCLI) generates deployable packages, which can not be modified once deployed. During the build process the owner of a package has full control over all files and dependencies.

2. Microservice Architecture

Vorteil follows a unikernel-like approach in a sense that it uses a single address space and can run only
one application at a time (multiple threads are possible, of course). This means that each service runs in it's own small, isolated virtual machine.
These machines can be orchestrated to form a full application.

Try it out with the easy-to-follow [getting started guide](/quick/first_run)

<center>
<a href="http://www.youtube.com/watch?feature=player_embedded&v=NKjCnMLd-Rs
" target="_blank"><img src="http://img.youtube.com/vi/NKjCnMLd-Rs/0.jpg"
alt="IMAGE ALT TEXT HERE" width="480" height="360" border="0" /></a>
</center>
