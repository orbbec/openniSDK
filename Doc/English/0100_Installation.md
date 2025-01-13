# Installation

## System Requirements

| OS    | Requirements                                     | Details                                               |
| ------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Windows | 1、Windows 7, 8 and 10, 32-bit and 64-bit <br />2、x86-based processor @ 1.8+ ghz <br />3、USB 2.0 <br />4、4 gigabytes of RAM | Supports development with Visual Studio 2013/2015/2017/2019. Visual Studio 2017/2019 use the same package with Visual Studio 2015. |
| Linux   | 1、Ubuntu 14.04 or later(Ubuntu 20.04), x86_64, arm, arm64 <br />2、amd64-based processor @ 1.8+ ghz<br />3、USB 2.0 <br />4、1 gigabyte of RAM | GCC 4.9 and Clang 3.5 have both been extensively tested, but any compiler with support for C++11 should be compatible,including GCC 4.9 or better, Clang 3.1 or better, and Android NDK r9e or better. |
| Android | 1、Android OS 4.4.2 (KitKat) + <br />2、ARMv7a/ARM64v8a processor @ 1.5 ghz+ <br />3、USB 2.0 host support (OTG-capable) <br />4、512 megabytes of RAM | GCC 4.9 and Clang 3.5 have both been extensively tested, but any compiler with support for C++11 should be compatible,including  GCC 4.9 or better, Clang 3.1 or better, and Android NDK r9e or better. |

# Windows Installation

## Installing the Driver

First, download the latest  [Orbbec Sensor Driver for Windows]( https://orbbec3d.com/), then run the installer:

1.Click install to start install process.

![](./images/install_driver_01.png)

2.While in the dirver installer wizard window, click next.

![](./images/install_driver_02.png)

3.If you see panel like this, the dirver installed right.

![](./images/install_driver_03.png)

4.After install finished, click finish to complete

![](./images/install_driver_04.png)

5.When you complete install the driver, you can connect the device to your PC,
then in your device manager, you will see the new orbbec deivce.

![](./images/install_driver_05.png)

## Download the SDK

We provide SDK versions list blow:

-   OpenNI SDK for Windows 32-bit
-   OpenNI SDK for Windows 64-bit
-   OpenNI SDK for Linux 32-bit
-   OpenNI SDK for Linux 64-bit
-   OpenNI SDK for Linux arm
-   OpenNI SDK for Linux arm64
-   OpenNI SDK for Android arm64-v8a
-   OpenNI SDK for Android armeabi-v7a

[Download]( https://orbbec3d.com/) the corresponding version SDK.

## Setup for Visual Studio

1.Copy OpenNI2 SDK sdk/windows to a folder,  for example called  \$OpenNI_SDK_HOME.

2.Open a new project or an existing one.

3.In the Visual Studio menu, open the Project menu and choose Project properties.
![](./images/installation_vs_project_properties_en.png)

4.In the C/C++ section, under the General node, find the "Additional Include Directories" and add "$(OpenNI_SDK_HOME)\include".

![](./images/installation_vs_include.png)

5.In the Linker section, under the General node, find the "Additional Library Directories" and add "$(OpenNI_SDK_HOME)\x64-Release".

![](./images/installation_vs_lib_dir.png)

6.In the Linker section, under the Input node, find the "Additional
Dependencies" and add OpenNI2.lib。

![](./images/installation_vs_libs.png)

## Run the NiViewer.exe

In the $(OpenNI_SDK_HOME)\x64-Release\ folder，run the NiViewer.exe, you will see below：

![](./images/nivewer_demo_res.png)


# Linux Installation

## Installing the Driver

Devices under the Linux platform are loaded as common CMOS cameras. Currently, the popular Linux platforms have built-in corresponding drivers, and no additional installation is required.

But installation prerequisites are required：

freeglut3 


## Configure the OpenNI2 SDK in the Makefile

### Library files

- libOpenNI2.so
- OpenNI2/Drivers/libOniFile.so
- OpenNI2/Drivers/liborbbec.so

### Configuration files

- OpenNI.ini
- OpenNI2/Drivers/orbbec.ini

### Configuration in the Makefile

- Add the header Include directory to the Include directory
INC_DIRS = ../../Include \

- Add OpenNI2 to the Lib you use
USED_LIBS += OpenNI2

### Run Sample and NiViewer
1.First, connect the camera and computer, and check the device through the following command line:

```
username@ubuntu:~$ lsusb
```

At this point, you can view the PID/VID of the camera device, and then use the OpenNI SDK to view the depth image.

2.Obtain the SDK packet of the corresponding platform in the official developer community. Website: [OpenNI SDK for Linux](https://orbbec3d.com/)
This topic selects the Linux-x64 platform. Decompresses it after downloading. For more information about how to use the SDK, see Readme in the folder.

```
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ vi Readme
```

3.Next, install the Sample runtime environment. Follow the steps in the Readme document to install the necessary libraries, and then install and configure the environment. The command line is as follows:

```
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ sudo apt-get install build-essential freeglut3 freeglut3-dev
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ sudo ./install.sh
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ source OpenNIDevEnvironment
```

Note: You may need to modify the file permissions to run install.sh. You can use "ll" to view the permissions and "chmod" to modify the permissions, as follows:

```
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ ll
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65$ chmod 777 install.sh
```

4.Next, run provided Sample executable files in the Bin folder under the Sample path. Similarly, you need to use "chmod" to modify file permissions. Take SimpleViewer as an example. Run the "sudo" command to run the program. The command line is as follows:

```
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65/Sample/Bin$ chmod 777 SimpleViewer
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65/Sample/Bin$ sudo ./SimpleViewer
```

5.At the same time, there is a NiViewer executable file in the Tools Directory. Run the NiViewer by running the following command at the command line terminal:

```
username@ubuntu:~/OpenNI-Linux-x64-2.3.0.65/Tools$ ./NiViewer
```

You will see the following display:

![](./images/nivewer_demo_res.png)

# Android Installation

## Installing the Driver

Under the Android platform, since the underlying layer is based on the Linux platform, the corresponding driver of the camera has been built in, so no additional installation is required.

## Setup for Android Studio

### Library files

The libraries provided by the OpenNI2 SDK for Android users include two parts, five so dynamic library files and one jar file:
- libOniFile.so
- libOpenNI2.jni.so
- libOpenNI2.so
- liborbbec.so
- liborbbecusb2.so
- openni2.3.jar

### ini files

Two ini configuration files
- OpenNI.ini
- orbbec.ini

### Configure the OpenNI2 SDK in the Android Studio project

- Copy the library files to the libs directory of the project Module
![](./images/android_inlcude_so.png)
- Copy the ini  files to the app->src->main->asset->openni directory of the project Module
![](./images/android_openni_config.png)
- Respecify the jniLibs directory in the build.gradle configuration of the Module, and finally synchronize the entire project
![](./images/android_build_gradle.png)

## Run Android Sample
- Samples-android project structure

  ![](.\images\android_sample_project.png)

- Such as Depth output example

  ![](.\images\android_sample_depth0.png)