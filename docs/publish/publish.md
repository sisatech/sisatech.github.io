# Local Export

Although the main goal for vorteil.io is to publish directly into the cloud or datacentres, there is an option to export the application to different formats. This option is mainly to support existing deployment processes, so nothing needs to be changed to use vorteil.io with e.g. new projects.

Different hypervisors need different formats, so basically vorteil.io is supporting the major formats and all hypervisors should at least accept one fo them. The formats are:

* VMDK
* OVA
* VHD
* GCP (google cloud formatted tar)
* stream-optimized VMDK

!> Stream-optimized VMDKs are read-only disks!

To use the export functionality, simple select a **.vorteil** package or point to an existing binary and execute the **build** command:

**Example (Export package as vmdk)**:
```vcli
vcli build --format=vmdk mypackage.vorteil
```

Additionally the exported artifact can be changed during the build process with flags. E.g. it can be build with a different environment variables or command line arguments.

**Example (Export application with parameters)**:
```vcli
vcli build --format=vmdk --args='arg1' --var="MYENV=HELLO"
```

!> Building from a package does not allow to change the artifact with parameters due to vorteil's emphasis on immutablity.

# VMWare ESXi

# Goolge Cloud

For deloying to the Google Could Platform (GCP), a valid account is required. Additionally vcli needs credentials with adequate permissions to execute all required deployment commands. For this a so called service account is needed . This can be done in three simple steps after login in to [Google Cloud Platform](https://cloud.google.com/).

#### 1. Go to "Service Accounts"

From the main navigation in the upper left corner, go to *IAM > Service Accounts*

![alt text](/publish/gcp1.png "service account")

#### 2. Create Service Account

In the top navigation bar, select "Create Service Account"

![alt text](/publish/gcp2.png "create service account")

#### 3. Download JSON private key

After selecting the role for the service account and choosing JSON as private key format, the download of hte key should start automatically.
This key is needed later to create a deployment target in vcli.

![alt text](/publish/gcp3.png "get service account json key")

After downloading the key it is required to add it to vcli, to use it for deployments. During this process a bucket and a zone for the newly created images has to be specified. This is needed to upload the the application after converting it to a GCP-compatible format.

**Example:**
```vcli
vcli cloud new gcp /path/tp/key.json
```

This process only has to be executed once to setup the target. After that, it can be used for all future deployments to this target. The deployment can be initialized with a simple **cloud upload** command. The application to deploy can be either a binary or a **.vorteil** package.

**Example (Command and output):**
```vcli
vcli cloud upload gcp myapp

Using config file: hugo.vcfg
Using files: hugo.files
Configuration Summary:
 • Vorteil kernel 0.1.2
 • Automatically sized virtual disk with ext2 partition
 • 1 network card
 • 1 virtual filesystem redirect
Merging 1 directories
 • hugo.files
 8.03 MiB / 8.03 MiB [==============================================] 100.00% 0s
Connecting to Google Cloud Storage...
Accessing bucket: vorteil-demo...
Initializing new object: 862216640.tar.gz...
Uploading image
 10.00 MiB / 12.70 MiB [=================================>---------]  78.73% 32s
```

During those deployment steps, vcli converts the uploaded package to an image, which can be used to spin up new machines. The name of the image is a hash value and it can be seen during the upload process. In the former example, the image name would be "862216640".

![alt text](/publish/gcp4.png "images list")

After these steps new machines based on this image can be created. 

![alt text](/publish/gcp5.png "select custom image")
