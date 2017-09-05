# 快速入门指南

Vorteil开始很容易。你只需要做这三个简单的步骤。

## 步骤1  - 安装VCLI


VCLI是Vorteil命令行界面。它是您需要与Vorteil合作的唯一工具。

[VCLI安装指南](/zh-cn/vcli.md)

### Linux的

__步骤1：安装管理程序__


如果您还没有安装虚拟机管理程序，则以下命令将安装KVM：

		sudo apt-get install qemu-kvm
Linux上的其他支持的虚拟机管理程序是VMware Workstation，VMware Workstation Player和Oracle VirtualBox

###  Mac OS X

__步骤1：安装管理程序__


下载并安装您首选的管理程序软件：

[VirtualBox](https://www.virtualbox.org/)

[VMware Fusion](https://www.vmware.com/)

### Windows

__步骤1：安装管理程序__

下载并安装您首选的管理程序软件：

[VirtualBox](https://www.virtualbox.org/)

[VMware Workstation or Workstation Player](https://www.vmware.com/)

确保将相应的虚拟机监控程序[位置添加到路径中](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/).



如果您使用Bash，则在下次登录到计算机时，将自动完成命令。

## 第2步 - 获取Vorteil应用程序

您需要一个Vorteil应用才能运行。任何人都可以建立自己的Vorteil应用程序，但现在我们从官方的在线存储库中获取一个。我们将使用Sisa-Tech的HelloWorld应用程序包进行此快速入门演示。

		vcli apps pull sisatech/helloworld


此命令将软件包下载到VCLI的本地存储库中，以方便访问，组织和版本控制。

## 步骤3  - 编译并运行应用程序


现在我们有一个存储在本地存储库中的应用程序包，我们需要构建并运行它作为一个虚拟机。 HelloWorld软件包附带了VCLI运行所需的所有信息，因此除了运行它之外，您不需要执行任何操作。

		vcli apps run sisatech/helloworld


恭喜！您现在应该可以访问自己的计算机上的虚拟机上托管的HelloWorld网页 http://localhost:8080/.
