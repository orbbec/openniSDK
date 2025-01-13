# SDK knowledge base

Now that we've finished installing the OpenNI2 SDK and are familiar with the basics, let's move on to the four core SDK concepts -- OpenNI, Device, VideoStream, and VideoStreamRef.Understanding these concepts is of great importance to our later development and application.In addition, an in-depth understanding of these four concepts will be of great help to further research and development in the future as well as to quickly pick up new SDK features that may be released in the future.

## OpenNI

The OpenNI class is a static entry to the API, and every OpenNI2.0 application needs to use this class to initialize the SDK and drivers so that legitimate device objects can be created.The OpenNI class also defines a listener class and events that enable applications to be notified of events when a device connection, a device connection disconnect, and a device configuration change occurs.In addition, the OpenNI class provides a function to get version information for OpenNI and a function to wait for data frames to be generated from any stream in the list.

## Device

The Device class is an abstraction of a particular Device, either a hardware Device or a file Device recorded from a hardware Device.This class provides the ability to connect to a device and get configuration information about the device and the kind of flow the device supports.This class provides methods to query and modify device configuration parameters, including startup depth and color streams, and frame synchronization.In order to call the videostream.create () function, we need a pointer to the Device object as one of the parameters of the videostream.create () function. For application developers, using the Device to create and initialize the VideoStream is the most basic use of the Device class.Before creating the device object, the OpenNI::initialize() function must have been called to enable the API to get the device drivers in the system.

## VideoStream

Video streams are sequential streams of frames from a particular data source.Imagine a roll of old motion-picture film in which the video is sequentially recorded on a strip of film as a single image snapshot.Each image snapshot is a frame, and you can think of the entire movie as a stream, different from a movie in that the stream does not necessarily have an exact destination.

The VideoStream object encapsulates a separate VideoStream on the device. Once the VideoStream object is created, it can be used to start the data stream on the device and read the data frames from the device.The VideoStream class is the core of getting data in OpenNI. The VideoStream class provides the ability to read data manually in a loop and provides the definition of the event class and listener class for getting data in an event-driven manner.

In addition to the interface for getting data frames, the VideoStream class provides a series of functions to get information about a VideoStream object, such as the field of view, supported video modes, and supported maximum and minimum pixel values.In addition to getting the data, the VideoStream object is used to configure a property that specifies the stream and, in particular, to control clipping, mirroring, and video modes.

To create a flow, we need a pointer to a legitimate initialized device that supports the type of flow to be created.Multiple video streams can be created on the same sensor, which is useful when multiple modules of an application need to read frame data separately.

##  VideoStreamRef

The VideoFrameRef class is an abstraction of a video frame and its metadata.A video frame is the output of a particular video stream at a particular time.The output data contains a single frame (Color, IR, or Depth) and the corresponding metadata.

A VideoFrameRef class object does not actually hold the data in the frame, but merely a reference to the frame.This reference can be released by destroying the VideoFrameRef object or by calling the release() method.When the last reference of the frame is released, the data in the frame is actually released.

The most common way to get the VideoFrameRef object is to call videostream::readFrame().

The data referenced by the VideoFrameRef object is stored in an array of pixels.The type of each pixel is consistent with the specified pixel format.

