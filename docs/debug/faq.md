# FAQ
-----

## WHen starting an application, I'm getting the error *"Error: cannot automatically determine <app>: too many valid Vorteil packages in '.'"*

vcli’s run command tries to guess what it should run by looking in the current directory and finding a valid **.vorteil** Package. This error occurs when there are more than one of such packages in the current directory.

Adding the target to be run as an argument to the run command resolves the problem.

Example:
```vcli
vcli run helloworld.vorteil
```

## When running vcli, I'm getting the error *"Error: could not detect a supported hypervisor on the PATH".* 

vcli needs to use a third-party hypervisor to launch a virtual machine. It looks for VirtualBox, KVM and various VMware hypervisors on the PATH and in common install locations. vcli couldn’t find any of these hypervisors anywhere.

Make sure you have a supported hypervisor installed on your computer. If this error persists, add the hypervisor to your system’s PATH environment variable manually.

## Everything appears to have launched smoothly, a virtual machine is running and you see serial output on the virtual machine’s teminal, but I can not connect to the virtual machine with tcp, udp or http.

vcli doesn’t give up when the app it’s trying to launch requires a port that is already in use or requires admin permissions. If a desired port can’t be bound, a different port will be randomly chosen for the port-forwarding instead. 

If the configured ports can be used, vcli's output would be like:

```shell
Port forwarding:
  tcp: 8888 → 8888
```

But if port 8888 was unavailable, the number of the right of the arrow will be different and highlighted in yellow. Use this yellow number instead of “8888” in the url.


