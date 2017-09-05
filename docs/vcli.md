# VCLI Installation Guide

## Linux

### For Debian, Ubuntu, and variants

Run the following command in order to add our Debian repository.

		$ curl -s https://packagecloud.io/install/repositories/sisatech/vcli/script.deb.sh | sudo bash

Upon completion, VCLI can be installed with:

		$ sudo apt install vcli

Once complete, you can test the installation with the following command. If it returns the correct version you downloaded, VCLI is ready and working!

		$ vcli version

Congratulations! You're ready to get to work with the Vorteil Command Line Interface!

### For Linux distrobutions using rpm

Run the following command in order to add our RPM repository.

		$ curl -s https://packagecloud.io/install/repositories/sisatech/vcli/script.rpm.sh | sudo bash

Next, install VCLI using *yum* or *dnf*.

Once complete, you can test the installation with the following command. If it returns the correct version you downloaded, VCLI is ready and working!

		$vcli version

Congratulations! You're ready to get to work with the Vorteil Command Line Interface!

## Windows

Start by downloading the latest [Windows release of VCLI](https://github.com/sisatech/vcli/releases).

Extract the contents and place the .exe file in whichever directory is preferred (e.g. C:\Windows\vcli\), and ensure that this is located [within your system PATH](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/), so that VCLI can be called via Command Prompt.

Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, VCLI is ready and working!

		$ vcli version
NOTE: Close and open a new command prompt or powershell terminal to ensure the changes are applied. Alternatively, Windows may require a restart after adding new entries to the PATH.

Congratulations! You're ready to get to work with the Vorteil Command Line Interface!


## Mac OS X


Start by downloading the latest [Mac release of VCLI](https://github.com/sisatech/vcli/releases).

Extract and move the vcli binary file to a location in your system PATH (typically located at /usr/local/bin/):

		mv <path_to_vcli_binary> /usr/local/bin/
Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, VCLI is ready and working!

		$ vcli version
Congratulations! You’re ready to get to work with the Vorteil Command Line Interface!
