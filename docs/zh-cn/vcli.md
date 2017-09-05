# VCLI Installation Guide

## Linux

### For Debian, Ubuntu, and variants

The easiest way to download vcli for Linux is to get it from our debian repository. This method also automatically installs man-pages and bash autocompletion scripts.
First, add the Sisa-Tech public repository to your list of repositories.

		$ echo "deb https://sisatech.bintray.com/deb dev main" | sudo tee -a /etc/apt/sources.list
In case of an error message, Sisa-Tech's public keys may need to be added.

		$ apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61
Run a quick update.

		$ apt-get update
Next, simply apt-get vcli.

		$ apt-get install vcli
Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, the vcli is ready and working!

		$ vcli --version
Congratulations! You're ready to get to work with the Vorteil Command Line Interface!

### For other Linux flavours

Start by downloading the latest [Linux release of VCLI](https://github.com/sisatech/vcli/releases).

Extract and move the vcli binary file to a location in your system PATH (typically located at /usr/local/bin/):

		mv <path_to_vcli_binary> /usr/local/bin/
Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, the vcli is ready and working!

		$ vcli --version
Congratulations! You’re ready to get to work with the Vorteil Command Line Interface!


## Windows

Start by downloading the latest [Windows release of VCLI](https://github.com/sisatech/vcli/releases).

Extract the contents and place the .exe file in whichever directory is preferred (e.g. C:\Windows\vcli\), and ensure that this is located [within your system PATH](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/), so that VCLI can be called via Command Prompt.

Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, the vcli is ready and working!

		$ vcli --version
NOTE: Close and open a new command prompt or powershell terminal to ensure the changes are applied. Alternatively, Windows may require a restart after adding new entries to the PATH.

Congratulations! You're ready to get to work with the Vorteil Command Line Interface!


## Mac OS X


Start by downloading the latest [Mac release of VCLI](https://github.com/sisatech/vcli/releases).

Extract and move the vcli binary file to a location in your system PATH (typically located at /usr/local/bin/):

		mv <path_to_vcli_binary> /usr/local/bin/
Once you're done, you can test the installation by using the following command. If it returns the correct version you downloaded, the vcli is ready and working!

		$ vcli --version
Congratulations! You’re ready to get to work with the Vorteil Command Line Interface!
