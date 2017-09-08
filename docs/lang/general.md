# Supported Languages
---------------

vorteil.io's aim is to run applications without making changes to them ,so in general moving applications on vorteil.io should be without risk and too much overhead.

To minimize the effort vorteil.io has some tools to setup a project for a certain set of languages. If the languages you want to use, is not in the list of supported languages, a [project can be setup](/vcli/conf) and saved as a [template](/lang/general?id=managing-environments) for future use.  

The supported languages are:

* Go
* Node.js
* Python
* Java
* Ruby
* C# (mono)
* C#/F# (.net core)
* Rust

In general other generic ELF binaries hsould run as well, but needs to be tested for the individual use case.

## Managing environments

Environments make it easier to start a project from scratch and getting started wit h running the application on vorteil.io. There is a growing set of environments available for download. vcli manages the environments and can download and update them.

**Example (List all available environment):**

```vcli
vcli environments list --all
```

**Example (Downloading a environment):**
```vcli
vcli environments download python-2.7.12
```

**Example (List downloaded environment):**
```vcli
vcli environments list
```

## Using environments

Once one of the templates is downloaded, setting up a project consists of two simple steps.

##### Creating project folder

The process should start in a newly created, empty folder. Ideally the folder is named after the project you want to create. The environment to use, can be either downloaded before or it is getting downloaded when executing the **prepare** command.


##### Executing *prepare* command

The **prepare** command merge the downloaded environment with the existing application, files etc. to a new project in the folder is getting executed.

**Example (Go):**
```vcli
vcli prepare go /path/to/go/file
```

**Example (node.js):**
```vcli
vcli prepare nodejs-4.2.6 /path/to/nodejs/script
```

##### Advanced usage

During the prepare command all other vcli flags can be used. It is possible to merge serveral directories into this projects as well as setting environment variables or command line arguments.

**Example merging directories:**
```vcli
vcli prepare go /path/to/app --files=/more/files
```

**Example adding command line arguments:**
```vcli
vcli prepare go /path/to/app --args='arg1 arg2'
```


## Creating custom environment

Sometimes it is useful to create custom environments. Environments can be used to e.g. share logging configuration or libraries across projects or copy certificates from a central location into the app's file system.
 
An environment is basically a '.tar.gz' archive. It contains a binary, which can have any name (hereby referred to as *app*), a config file, which must be named *app*.vcfg, and a directory that will become the filesystem, which must be named *app*.files. The **prepare** command basically merges this environment over the top of an existing application configuration.  

**Example folder structure:**
```folder
- myenv
	- myenv
	- myenv.vcfg
	- myenv.files
```

There are two different types of applications when it comes to environments. Interpreted language based applications and executables. The difference is where the **prepare** command copies the application to during the prepare process.

As an example, go compiled applications need to be in the root of the project folder, whereas node.js files would reside in the project's file system and be executed by the node.js executable.

For the node.js exmaple, it is important that the **prepare** command can replace values in the **.vcfg** file with the application name being prepared. The *{APP}* variable can be used for that purpose.

**Example .vcfg for environment with {APP} variable:**
```yaml
...
env:
  bin: /usr/bin/nodejs
  args: "{APP}"
  vars: {}
vfs:
  filesystem: ext2
  redirects: []
  accelerate: []
...
```

Once the environment is ready to test, the directory just needs to be compressed and it is ready to be tested. As mentioned, the format is *.tar.gz* and the following example command has to be executed in the rceated environment folder.

**Example:**
```shell
tar -czf myenv.tar.gz *
```


To test the environment, the compressed archive needs to be copied into the *environments* folder in vcli's home directory, which is usually *${USER_HOME}/.vorteil*.
