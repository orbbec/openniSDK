# Changelog

## OpenNI2  SDK 2.3.0.86-beta6 Version update instructions

1、New Supported Astra Mini Pro，Gemini E/Gemini E Lite

# FAQ

## Questions about possibility

###  Q: Whether the OpenNI2 SDK supports color camera of UVC protocol

Currently not supported, for devices whose color camera in the sensor is UVC protocol, C++ recommends using the VideoCapture class provided in OpenCV to open the color camera and read the color stream. If the Android platform Orbbec module RGB is a UVC device, it needs to be opened with a third-party libuvc application. libuvc uses the GitHub-based open source framework UVCCamera: https://github.com/saki4510t/UVCCamera.

------

## About Sample Compilation

### Q:How to compile Sample for Windows, Linux and Android platforms

For sample compilation on Windows and Linux platforms, please refer to the readme document in the Samples directory provided when the SDK is released.

For the Android platform sample compilation, use the android studio tool.

## Questions about using

###  Q: "load_library failed: 87" on windows 7

Maybe you should install "Windows6.1-KB2533623" patch on your OS.

###  Q: The Windows vs2013/2015 x86 demo doesn't work, but the Windows vs2013/2015 x64 demo works fine.

Install vc++ x86 runtime libraries for vs2013/vs2015.

------


# Legal stuff

## Copyright

Copyright (c) 2015-2022 Orbbec

## Acknowledgements  

This software is based on following open source projects.

- libjpeg http://www.ijg.org/
- openni2 https://github.com/OpenNI/OpenNI2

