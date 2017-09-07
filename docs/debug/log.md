# Mounting & Logging
---------

During debugging logs are an important source of information to fix an issue in the application. There are several ways to get more information from vorteil.io and the running application. 

## vcli flags
-------------

The command line interface (vcli) comes with two important flags to increase output and makes the output easier to read and use. 

| Flag | Description |
|------| ------------|
|-e| Redirects stdout to the terminal where vcli started the application|
|--echo-file=filename| Writes serial output to named file|
|-d| Increases kernel debug. This flag shows kernel internal calls|
|--persist=filename.vmdk| Persists disk of the running application as vmdk |

**Example:**

```vcli
vcli -e -d --persist=/tmp/myfile.vmdk myapp
```

## Mounting disks
-----------------

With the **--persist** flag the virtual disk of the running application is gettig stored in VMDK format and can be used even after the application has been stopped. This is useful e.g. to mount the virtual disk later and inspect log or configuration files. The easiest way of mounting a virtual disk is using VMWare's disk mount utility. 

Disks use with vorteil.io have two partitions whereas the second partition contains the contents of the data directory, defined when starting an application. This is usually the **.files** directory.

**Example:**
```shell
vmware-mount /persisted/disk.vmdk 2 /empty/directory
``` 

## UDP logs
-------

An easier approach to see log files are vcli file redirects. These redirects are writing the contents to a UDP connection instead of writing it to a file. Redirects can be used for e.g. log files of the application, so the contents of the log files are getting streamed to the UDP target instead of the file. 

The file redirects have to be configured in the **.vcfg** file of the application.

```yaml
vfs:
  filesystem: ext2
  redirects:
  - src: /tmp
    dest: 127.0.0.1:2610
    protocol: udp
  - src: stdout
    dest: 127.0.0.1:2610
    protocol: udp
``` 

Additionally **stdout** can be used as a filename, which redirect all serial output to the UDP target as well.
