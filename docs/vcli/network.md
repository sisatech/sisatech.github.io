# Network

VCLI supports adding up to four network cards to a virtual machine, but not all tools and environments will support this number.

## VCLI Port Mapping

VCLI launches virtual machines with with port forwarding if there are ports defined in the Vorteil Configuration file or via the --port flag.

VCLI doesn’t give up when the app it’s trying to launch requires a port that is already in use. If a desired port can’t be bound, a different port will be randomly chosen for the port-forwarding instead. Normally VCLI’s output will have a section that looks like the following:

```bash
Port forwarding:
tcp: 8888 → 8888
```

But if port 8888 was unavailable, the number of the right of the arrow will be different and highlighted in yellow. In this case the number on the right will be highlighted in yellow, and will represent the port you should actually use in order to connect to the desired port in the virtual machine.
