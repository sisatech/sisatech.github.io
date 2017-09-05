## environments
Manage Vorteil environments.

To build a Vorteil Application the binary that will be executed needs to be
singled out. For compiled languages like C or Go this results in intuitive vcli
commands such as 'vcli run myapp'. For interpreted languages like Java, Python,
or Nodejs, the process is less intuitive because the binary being run is the
interpreter, whilst the interesting program is simply an argument to it.

To make one of these programs run as a Vorteil Application the user would need
to target the interpreter as the buildable binary, add the user's program (and
any dependencies) to the filesystem, and adjust the binary args to target the
user's program. This is convoluted and tedious. To simplify the use of
interpreted language programs, vcli can apply a user's program to an
'environment', which includes the interpreter and any dynamically-linked
libraries it depends upon.

Use the 'environments' subcommands to download and manage environments. Use the
'vcli prepare' command to apply an environment to an application.


#### delete
Delete a local Vorteil environment

#### download
Download a Vorteil environment from an online repository

#### list
List available Vorteil environments
