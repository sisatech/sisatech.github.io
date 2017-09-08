# Project Setup

VCLI is capable of running any Linux-compiled ELF binary and doesn't need anything extra, but the applications themselves will often need a customized runtime environment or supporting files. A Vorteil Project is a structured directory layout with naming conventions that allows VCLI to automatically determine which files to use. In this section you'll learn how to set up a project to add these extra components.

VCLI uses the following components to build a Virtual Machine:
- An executable Linux-compiled ELF binary.
- Any number of filesystem directories.
- Any number of Vorteil configuation (.vcfg) files.

An ideal Vorteil Project should be a directory containing the following components, where NAME can be anything:
- NAME *- the binary*
- NAME.files *- a directory containing the files for the filesystem*
- NAME.vcfg *- a Vorteil configuration file*

## The Binary

The binary is the single most important part of the VCLI build process, and the only one that is non-optional. It is the executable file that you want to run in a virtual machine. For the VCLI commands that require one, an optional argument can be provided to specify which file to run.

VCLI commands that can take an optional TARGET argument:
```bash
vcli run [TARGET]
vcli build [TARGET]
vcli package [TARGET]
```

The TARGET argument is quite flexible. If it is a path directly to a binary then there is no ambiguity, but it can also be a path to a directory containing a Vorteil Project. If TARGET is a Vorteil Project then it is important that there is only one executable binary and there are no Vorteil Packages present, otherwise VCLI might be unable to determine what should be used. If TARGET is not provided VCLI will use "." as its target: the current working directory will be assumed to be a Vorteil Project.

## The Filesystem

Many applications need supporting files. Even if your program doesn't rely on any files for its own logic, it may have been compiled to load Dynamically Linked Libraries during its execution. These files obviously need to be added to the Virtual Machine Disk so that they can be found when they are needed. VCLI needs to know where to find these files in order to include them.

Once VCLI knows what binary to use, it will automatically look for a directory with the same filepath, but with ".files" appended.

The --files flag can be used to manually target one or more directories to be used. If **any** directories are targeted with the --files flag then all directories must be targeted this way (VCLI won't automatically look for the ".files" directory). To target multiple directories the --files flag simply needs to be used repeatedly. If multiple directories are specified they will be logically merged over the top of each other in the order they were specified. The original files will never be altered.

!> The **run** and **build** commands are capable of using a Vorteil Package instead of an ELF binary. Vorteil Packages are considered to be immutable, and as such any and all flags that affect the runtime environment or the files on the disk will be intentionally ignored, with the exception of the --debug flag. You must unpack Vorteil Packages in order to make changes to them.

## The Configuration File

The Vorteil Configuration File contains information affecting a number of aspects of a Vorteil Application, from runtime settings to Virtual Disk build instructions, as well as metadata used by management tools to describe the Package. For a detailed overview of the things that can be done in a configuration file, see [Configuration](configuration.md).

Once VCLI knows what binary to use, it will automatically look for a configuration file with the same filepath, but with ".vcfg" appended.

The --config flag can be used to manually target one or more configuration files to be used. If **any** configuration files are targeted with the --config flag then all configuration files must be targeted this way (VCLI won't automatically look for the ".vcfg" file). To target multiple configuration files the --config flag simply needs to be used repeatedly. If multiple configuration files are specified they will be logically merged over the top of each other in the order they were specified. The original files will never be altered. Any and all fields in a configuration file can be left blank, which will prevent them from overwriting the values in other configuration files.

Any important values that remain unset after all configuration files have been processed will be filled in by VCLI with useful defaults. Whenever the --config flag can be provided, many additional flags become available to override configuration file settings.

!> The **run** and **build** commands are capable of using a Vorteil Package instead of an ELF binary. Vorteil Packages are considered to be immutable, and as such any and all flags that affect the runtime environment or the files on the disk will be intentionally ignored, with the exception of the --debug flag. You must unpack Vorteil Packages in order to make changes to them.

## Interpreted Language Programs

Interpreted language programs are slightly more complicated because the executable binary is actually the interpreter itself, and your program is generally an argument to it. In these cases it is important to remember to use the interpreter as the binary itself, and put the program you want to run in the filesystem directory. You will also need to adjust the configuration file to provide the interpreter with the correct arguments to launch your program. The [prepare](prepare) command is designed to simplify this process.

## Dynamically Linked Libraries
