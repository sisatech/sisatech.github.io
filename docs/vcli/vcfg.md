# Vorteil Configuration File

The Vorteil Configuration file is a YAML file containing metadata and settings used by VCLI and other tools to generate, run, and manage Vorteil Applications and Packages.

The following is a commented and valid template for a Vorteil Configuration file.

```bash
# Vorteil application config YAML

# Descriptive information about the function and purpose of the application goes
# here. This information is used by programs that display information about a
# package, such as vcli's "apps info" command or vms' marketplace.
info:

# # Full name of the application.
  name: ""

# # Creator of the application.
  author: ""

# # A description, blurb, or notes describing the application.
  #
  # example
  #
  # description: >
  #   Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis tincidunt
  #   pulvinar turpis non cursus. Nam imperdiet cursus elit id rhoncus.
  description: ""

# # A link to a web page for the application.
  url: ""

# # The release date of the application
  #
  # example
  #
  # date: 02 Jan 06 15:04 MST
  date: 0001-01-01T00:00:00Z

# # Version of the application.
  version: ""

# Settings to alter the run-time environment for the application are here.
env:

# # The zeroth argument to be passed to the binary. This should typically be the
  # name of the binary itself, or a full path to where the binary needs to think
  # it exists.
  #
  # example
  #
  # bin: /usr/bin/java
  bin: ""

# # The command line arguments to be passed to the binary after the zeroth arg.
  # These arguments can include environment variables to be processed during
  # runtime.
  #
  # example
  #
  # args: "arg --flag=$VAR"
  args: ""

# # The environment variables as "KEY: VALUE" pairs. The environment variables
  # are processed in order, and can be used to define others using standard
  # shell syntax.
  #
  # example
  #
  # vars:
  # - HOME=/home
  # - USER=root
  # - VORTEIL_HOME=$HOME/vorteil
  vars: {}

# Settings to alter the behaviour of the filesystem go here.
vfs:

# # The filesystem implementation to build the disk with. Currently only 'ext2'
  # is supported.
  filesystem: ext2

# # Inodes is the minimum number of inodes the filesystem should support.
  inodes: 16384

# # Define special rules when for the virtual filesystem to enact when the
  # application attempts to write to a named file. This is a easy, for example,
  # forward the data sent to a log file out to a network logging server.
  #
  # example
  #
  # redirects:
  # - src: /debug.log
  #   dest: 10.0.0.1:8000
  #   protocol: udp
  redirects: []

# Configure network settings here.
network:

# # Specify the hostname for the VM to use. If left undefined it will be
  # automatically generated from the application name. A defined value is
  # static, which can cause problems if multiple copies of the same VM need to
  # be run at the same time. Leave this setting blank to avoid this problem.
  hostname: ""

# # Specify DNS servers here.
  dns: []

# # Specify network card configurations here. Up to four network cards can be
  # defined. The 'ip' field can be set to "dhcp" and the other fields left blank
  # in order to use DHCP.
  #
  # example
  #
  # nics:
  # - ip: dhcp
  # - ip: 10.0.0.1
  #   mask: 255.255.255.255
  #   gateway: 255.255.255.255
  nics:
  - ip: dhcp

# # List ports the VM will listen on here. A port should specify a protocol
  # (either udp, tcp, or http), and the port number, as well any network cards
  # it applies to. The cards list can be left blank to apply the rule to all
  # network cards.
  #
  # This information will be used by tools that launch a VM in a
  # context-relevant way. For example, vcli will use this information to define
  # port mappings with NAT. Other services could use this information to modify
  # firewall rules.
  #
  # example
  #
  # ports:
  # - port: 80
  #   protocol: http
  #   cards: 1
  # - port: 8080
  #   protocol: tcp
  #   cards: 1,3
  # - port: 1234
  #   protocol: udp
  #   cards:
  ports: []

# Advanced system settings can be configured here.
system:

# # The maximum number of available file descriptors.
  max-fds: 1024

# # Up to four NTP time servers can be specified.
  ntp-servers:
  - 0.pool.ntp.org
  - 1.pool.ntp.org
  - 2.pool.ntp.org
  - 3.pool.ntp.org

# Instructions for the virtual disk compiler can be configured here.
build:

# # The version of the Vorteil kernel to use. This is specified here to ensure
  # immutability of an application even as the kernel is updated over time.
  kernel: 0.1.2

# # The size of the filesystem in megabytes can be specified here. This number
  # does not reflect the actual size of the virtual disk. Leaving this value
  # set to '0' will tell the disk compiler to automatically choose the size of
  # the virtual disk, which will be big enough to include all provided files
  # with a little bit of leeway for temporary files.
  disk-size: 0

# Instructions for any tool that launches Vorteil VMs can be configured here.
vm:

# # The recommended number of virtual CPUs to assign to the VM.
  cpus: 1

# # The recommended amount of virtual ram to assign to the VM, in megabytes.
  memory: 128

```
