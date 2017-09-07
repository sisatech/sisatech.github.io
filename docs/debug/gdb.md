# Using gdb
-----------

Although the development process and debugging process should not change using vorteil.io, sometimes it might be required to debug the running application. Therefore vcli has gdb enabled, if the application runs in debug mode. 

```vcli
vcli -d -e yourapp
```

Turning on debug with the -d flag adds additional kernel output to the screen and starts the gdb server of KVM, VirtualBox or VMWare Workstation/Player and can be used like in other applications. The following script is an example for a .gdbinit file:

```.gdbinit
set arch i386:x86-64
target remote localhost:1234
set step-mode on
set pagination 
break *0x400000
```

This example would stop the hypervisor from executing at memory location 0x400000. 

!> gdb on VMWare uses port 8864, not 1234
 
