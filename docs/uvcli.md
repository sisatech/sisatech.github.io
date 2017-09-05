# Using VCLI

Now that you've installed VCLI time to see what it can do :).
For demo sake we will use an application for a Hugo Website which can be found via our pull method.

## run
The run command is used to launch your application in a specific hypervisor you have laid out more information can be [found out here](quickstart.md).

		$vcli run [FILENAME]

Upon success the application should launch in your chosen hypervisor and display logs of the application running.
## build
Build is a step before the run command. The build command allows you to build the vmdk. If you would like to test it in other aspects

		$vcli build [FILENAME]

Upon success the .vmdk file should appear next to the application you tried to build.
## vcfg
### template
The vcfg template functionality provides you a case of generating a vcfg file before you package or run your application.

		$vcli vcfg template

On success the directory you are currently in should now have an app.vcfg file. Which you can use by editing it manually or using our in client editor.
### new
Vcli offers the functionality of creating a new vcfg from scratch in their editor. Below you can either omit the file name and the file generated will be app.vcfg or you can give it a name to make the config

		$vcli vcfg new [FILENAME]

Upon success your terminal should now be displaying an editor to make changes to the file. The file should appear where the command was sent.

### edit
Vcli comes with its own command line editor. Which allows us to easily access the vcfg and save.

		$vcli vcfg edit [FILENAME]

Upon success your terminal should now be displaying an editor to make changes to the file. The file should appear where the command was sent.

## package
To package an application using vcli create a folder and place the binary, vcfg or other related build files into the folder. Feel free to leave the vcfg out as it will auto generate one for you as well.

 		$vcli package hugo

Now if vcli has successfully built your package you should see a hugo.vorteil package in the same directory as the folder you packaged.
## unpack
To unpack an application make sure you go to the path of the application our example here is hugo.vorteil. You can also link the entire path to the application as the filename. We find its easier to be in the directory you are working on.

		$vcli unpack hugo.vorteil

Now if it has successfully unpacked you should fine a folder called hugo. Which will contain files, binary and config.
