# Tutorials
## Build a File Server
We've already demonstrated how easy it is to get up and running with Vorteil. Now it's time to see how it can be used to build more complicated applications than just a simple 'Hello World'.

The available Vorteil alpha currently supports Go applications.

Please ensure that you have correctly installed Golang on your machine prior to building applications for use with Vorteil.

The following code creates a simple web host:

	package main

	import (
		"fmt"
		"io"
		"net/http"
		"os"
		"path/filepath"
	)

	func main() {

		fmt.Printf("Hello %s\n", os.Args[1])

		http.HandleFunc("/", handler)
		http.ListenAndServe(":8080", nil)

	}

	func handler(w http.ResponseWriter, r *http.Request) {

		fileToRead := filepath.Join(os.Getenv("MYFILES"), r.URL.Path)

		f, err := os.Open(fileToRead)
		if err != nil {
			io.WriteString(w, "File not found")
		} else {
			io.Copy(w, f)
		}
	}

This code creates a basic web server on port 8080, accepts one program argument, and makes use of the environment variable, "MYFILES", which contains the filepath to the directory which will be used to create the filesystem.

There are very few steps required in order to get this up and running with Vorteil. All we need to do is create a config file, and compile the source code as an ELF binary.

### Compile the Source Code as ELF Binary
While Vorteil is not a Linux or Unix variant, it does support ELF binaries as applications.

Thankfully, Go makes the process of compiling an ELF binary very easy. You can build this source code into the appropriate format, from any operating system, by building it with the following command:

		env GOOS=linux GOARCH=amd64 go build -tags netgo
This instructs Go to compile the source code for use on Linux operating systems, using amd64 architecture. The "-tags netgo" ensures that included libraries are statically linked, rather than dynamically.

### Create a Vorteil Config file
To generate a generic config file with some default presets, run the following command:

		vcli config standard <binary name>
To open the new config file in the VCLI editor:

		vcli config edit <binary name> 	

Note: Windows users will have to open the resulting file and manually edit the required fields.
Once the editor is open, navigate to the 'app settings' section, where you will find 'binary args' and 'system envs'. Enter your name as one of the binary args, and path of the file to get content from. If these files are going to be located within the root directory of the Vorteil app, simply type "MYFILES=./"

When you are satisfied with the settings within your config file, press 's' to save and quit.

### Running the Server with Vorteil
Now that we have an ELF Binary generated from our source code, and an appropriate config file, we are ready to run our Vorteil app!

Note: This step will required that you have at least one of the supported hypervisors installed.

Before we launch the server, let's create a simple 'index.html' file, and save it in the directory that will be passed to VCLI when we run the server.


		<!DOCTYPE html>
		<html>
			<head>
				<meta charset="utf-8">
				<title>My Vorteil File Server</title>
			</head>
			<body>
				<h1>Hello world!</h1>
			</body>
		</html>


Keep in mind that our server will listen on port 8080, and needs a directory to build into it's filesystem. To run your app with Vorteil, run the following command:

		vcli run <binary name> --port-map=0:8080:8080 --files=<path to files directory>
Note: you may specify an alternate hypervisor to use with the --hypervisor flag.

This will build and run your app, launching it with the selected (or default) hypervisor.

To see your server in action, if you are using KVM you can click here.

Otherwise, browse to the VM and filepath to the file you wish to display - e.g. "http://localhost:8080/index.html")

### Version Control with the VCLI Repository
Now that you've successfully built a functioning file server with Vorteil, you may want to create a 'checkpoint' that you can revert to at any point in the future. Thanks to VCLI, this is easy!

To add your binary/config file to VCLI's local repository, run the following command:

		vcli repository import <binary name>
Note: You can also add unique tags to your repository entries by using 'vcli repository tag'

You will be able to see that your project has now been saved to the repository by running:

		vcli repository list
Or, for a more detailed view:

		vcli repository list <binary name>
The next time you import your project to the repository, it will be entered as a new version, without overwriting the previously stored versions.
To test this functionality, change the binary argument within your config file from your name, to "everybody". Run the previous command to import the new version to the repository. If at any point you wish to load a previous version from the repository, run the following command:

		vcli repository export <binary name> --ref=<version reference>
Note: Each version's 'reference' can be seen on the detailed repository list view. If no --ref is passed to VCLI, the latest version will be used.)

You now have a functional file server, with version control! Wasn't that easy?


## Build a Hugo Website

In this tutorial, you will create your own Hugo website, running as a Vorteil app.

Download the project archive ([Linux/Mac](https://storage.googleapis.com/vorteil/vcli-demo-platforms/hugo-demo.tar.gz), or [Windows](https://storage.googleapis.com/vorteil/vcli-demo-platforms/hugo-demo.zip)), and let's get started!

Extract the archive into your current working directory.

Create a webpage for your Hugo website to server, for example the below:


		<!DOCTYPE html>
		<html>
		    <head>
		        <meta charset="utf-8">
		        <title>My Hugo Website</title>
		    </head>
		    <body>
		        <h1>Hugo is working!</h1>
		    </body>
		</html>


Create a Vorteil config file for hugo, and set the "binary args" to: 'server --port 8080'.

		vcli config new hugo
Now, run the following command to pass the hugo website directory, port, and hugo binary to VCLI:

		vcli run hugo --port-map=0:8080:80 --files=<path-to-hugo-website-root-directory>
Your newly compiled Vorteil app will launch using your preferred hypervisor.

To see your website, if you are using KVM as your hypervisor [click here](http://localhost:8080/), otherwise browse to the VM on port 80.

Congratulations! You have just built your own hugo website with Vorteil!
