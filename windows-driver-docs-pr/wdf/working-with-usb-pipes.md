---
title: Working with USB Pipes
description: Working with USB Pipes
ms.assetid: d5422ff2-de1e-4a77-8b3c-0b2917b1d9ca
keywords:
- framework objects WDK KMDF , USB pipe objects
- USB pipes WDK KMDF
- pipe objects WDK KMDF
- USB I/O targets WDK KMDF , USB pipes
- continuous readers WDK USB
- resetting pipes WDK KMDF
- sending URBs WDK KMDF
- USB request blocks WDK KMDF
- URBs WDK KMDF
- stopping pipes WDK KMDF
- writing to pipes WDK KMDF
- reading from pipes WDK KMDF
- input pipes WDK KMDF
- output pipes WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Working with USB Pipes


The framework represents each pipe in a USB interface as a framework USB pipe object. When a driver [configures a USB device](working-with-usb-devices.md#selecting-a-device-configuration), the framework creates a framework USB pipe object for each pipe in each selected interface. Pipe object methods enable a driver to perform the following operations:

-   [Obtain pipe information.](#obtaining-pipe-information)

-   [Read from a pipe.](#reading-from-a-pipe)

-   [Write to a pipe.](#writing-to-a-pipe)

-   [Stop or reset a pipe.](#stopping-and-resetting-a-pipe)

-   [Send a URB to a pipe.](#sending-a-urb-to-a-pipe)

### <a href="" id="obtaining-pipe-information"></a> Obtaining Pipe Information

After calling [**WdfUsbInterfaceGetConfiguredPipe**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbinterfacegetconfiguredpipe) to obtain a handle to a framework USB pipe object, your driver can call the following methods that the USB pipe object defines for obtaining information about the USB pipe:

<a href="" id="---------wdfusbtargetpipegetiotarget--------"></a>[**WdfUsbTargetPipeGetIoTarget**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipegetiotarget)  
Returns a handle to the I/O target object that is associated with a USB pipe. The driver can pass this handle to [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend).

<a href="" id="---------wdfusbtargetpipegetinformation--------"></a>[**WdfUsbTargetPipeGetInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipegetinformation)  
Retrieves information about a USB pipe and its endpoint.

<a href="" id="---------wdfusbtargetpipegettype--------"></a>[**WdfUsbTargetPipeGetType**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipegettype)  
Returns the type of a USB pipe.

<a href="" id="---------wdfusbtargetpipeisinendpoint--------"></a>[**WdfUsbTargetPipeIsInEndpoint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeisinendpoint)  
Determines whether a USB pipe is connected to an input endpoint.

<a href="" id="---------wdfusbtargetpipeisoutendpoint--------"></a>[**WdfUsbTargetPipeIsOutEndpoint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeisoutendpoint)  
Determines whether a USB pipe is connected to an output endpoint.

<a href="" id="---------wdf-usb-pipe-direction-in--------"></a>[**WDF\_USB\_PIPE\_DIRECTION\_IN**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdf_usb_pipe_direction_in)  
Determines whether a USB endpoint is an input endpoint.

<a href="" id="---------wdf-usb-pipe-direction-out--------"></a>[**WDF\_USB\_PIPE\_DIRECTION\_OUT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdf_usb_pipe_direction_out)  
Determines whether a USB endpoint is an output endpoint.

For related information, see [How to enumerate USB pipes](https://docs.microsoft.com/windows-hardware/drivers/usbcon/).

### <a href="" id="reading-from-a-pipe"></a> Reading from a Pipe

To read data from a USB input pipe, your driver can use any (or all) of the following three techniques:

-   Read data synchronously

    To read data synchronously from a USB input pipe, your driver can call the [**WdfUsbTargetPipeReadSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipereadsynchronously) method. This method builds and sends a read request, and it returns after the I/O operation has completed.

-   Read data asynchronously

    To read data asynchronously from a USB input pipe, your driver can call the [**WdfUsbTargetPipeFormatRequestForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforread) method to build a read request. Then the driver can call [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send the request asynchronously (or synchronously).

-   Read data asynchronously and continuously

    A *continuous reader* is a framework-supplied mechanism for ensuring that a read request is always available to a USB pipe. This mechanism guarantees that the driver will always be ready to receive data from a device that provides an asynchronous, unsolicited input stream. For example, a driver for a network interface card (NIC) might use a continuous reader to receive input data.

    To configure a continuous reader for an input pipe, the driver's [*EvtDevicePrepareHardware*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_prepare_hardware) callback function must call the [**WdfUsbTargetPipeConfigContinuousReader**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeconfigcontinuousreader) method. This method queues a set of read requests to the device's I/O target.

    Also, the driver's [*EvtDeviceD0Entry*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_d0_entry) callback function must call [**WdfIoTargetStart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstart) to start the continuous reader and the driver's [*EvtDeviceD0Exit*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_d0_exit) callback function must call [**WdfIoTargetStop**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstop) to stop the continuous reader.

    Each time that data is available from the device, the I/O target will complete a read request and the framework will call one of two callback functions: [*EvtUsbTargetPipeReadComplete*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nc-wdfusb-evt_wdf_usb_reader_completion_routine), if the I/O target successfully read the data, or [*EvtUsbTargetPipeReadersFailed*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nc-wdfusb-evt_wdf_usb_readers_failed), if the I/O target reports an error.

    If you do not supply the optional [*EvtUsbTargetPipeReadersFailed*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nc-wdfusb-evt_wdf_usb_readers_failed) callback, the framework responds to a failed read attempt by sending another read request. Therefore if the bus is in a state where it is not accepting reads, the framework continually sends new requests to recover from a failed read.

    After a driver has called [**WdfUsbTargetPipeConfigContinuousReader**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeconfigcontinuousreader), the driver cannot use [**WdfUsbTargetPipeReadSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipereadsynchronously) or [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send I/O requests to the pipe unless the driver's [*EvtUsbTargetPipeReadersFailed*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nc-wdfusb-evt_wdf_usb_readers_failed) callback function is called and returns **FALSE**.

By default, the framework reports an error if your driver specifies a read buffer that is not a multiple of the pipe's maximum packet size. Your driver can call [**WdfUsbTargetPipeSetNoMaximumPacketSizeCheck**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipesetnomaximumpacketsizecheck) to disable this test of read buffer sizes.

For related information, see:

-   [How to send USB bulk transfer requests](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)
-   [How to transfer data to USB isochronous endpoints](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)
-   [How to use the continuous reader for reading data from a USB pipe](https://docs.microsoft.com/windows-hardware/drivers/usbcon/)

### <a href="" id="writing-to-a-pipe"></a> Writing to a Pipe

To write data to a USB output pipe, your driver can use one (or both) of the following techniques:

-   Write data synchronously

    To write data synchronously to a USB output pipe, your driver can call the [**WdfUsbTargetPipeWriteSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipewritesynchronously) method. This method builds and sends a write request, and it returns after the I/O operation has completed.

-   Write data asynchronously

    To write data asynchronously to a USB input pipe, your driver can call the [**WdfUsbTargetPipeFormatRequestForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforwrite) method to build a write request. Then the driver can call [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send the request asynchronously.

For related information, see [How to send USB bulk transfer requests](https://docs.microsoft.com/windows-hardware/drivers/ddi/index).

### <a href="" id="stopping-and-resetting-a-pipe"></a> Stopping and Resetting a Pipe

Your driver can call the following methods to stop or reset a USB pipe:

<a href="" id="---------wdfusbtargetpipeabortsynchronously--------"></a>[**WdfUsbTargetPipeAbortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeabortsynchronously)  
Synchronously sends a request to stop a USB pipe.

<a href="" id="---------wdfusbtargetpipeformatrequestforabort--------"></a>[**WdfUsbTargetPipeFormatRequestForAbort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforabort)  
Formats a request to stop a USB pipe. The driver can call [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send the request synchronously or asynchronously.

<a href="" id="---------wdfusbtargetpiperesetsynchronously--------"></a>[**WdfUsbTargetPipeResetSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpiperesetsynchronously)  
Synchronously sends a request to reset a USB pipe.

<a href="" id="---------wdfusbtargetpipeformatrequestforreset--------"></a>[**WdfUsbTargetPipeFormatRequestForReset**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforreset)  
Formats a request to reset a USB pipe. The driver must call [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send the request synchronously or asynchronously.

If your driver's USB target [completes](completing-i-o-requests.md) an I/O request with an error status value, your driver should do the following:

1.  Stop the pipe, and cancel any additional I/O requests that the driver has sent to the USB target, if the target has not completed the requests.

    Call [**WdfIoTargetStop**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstop) with the [**WdfIoTargetCancelSentIo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/ne-wdfiotarget-_wdf_io_target_sent_io_action) flag set.

2.  Synchronously send an abort request to the pipe.

    Call [**WdfUsbTargetPipeAbortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeabortsynchronously), or call [**WdfUsbTargetPipeFormatRequestForAbort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforabort) followed by [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) with the [**WDF\_REQUEST\_SEND\_OPTION\_SYNCHRONOUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/ns-wdfrequest-_wdf_request_send_options) flag set.

3.  Synchronously send a reset request to the pipe.

    Call [**WdfUsbTargetPipeResetSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpiperesetsynchronously), or call [**WdfUsbTargetPipeFormatRequestForReset**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforreset) followed by [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) with the [**WDF\_REQUEST\_SEND\_OPTION\_SYNCHRONOUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/ns-wdfrequest-_wdf_request_send_options) flag set.

4.  Restart the pipe.

    Call [**WdfIoTargetStart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstart).

5.  Resend the I/O request that failed, and all I/O requests that followed the failed request.

After a significant number of multiple failures, the driver should attempt to reset the USB port by doing the following:

1.  Stop all active pipes, and cancel any additional I/O requests that the driver has sent to each pipe's USB target, if the target has not completed them.

    For each active pipe, call [**WdfIoTargetStop**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstop) with the [**WdfIoTargetCancelSentIo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/ne-wdfiotarget-_wdf_io_target_sent_io_action) flag set.

2.  Synchronously send a request to reset the USB port.

    Call [**WdfUsbTargetDeviceResetPortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdeviceresetportsynchronously).

3.  Restart the pipes.

    Call [**WdfIoTargetStart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetstart) for each pipe that the driver stopped.

4.  Resend the last I/O request that failed, and all I/O requests that followed the failed request.

For related information, see [How to recover from USB pipe errors](https://docs.microsoft.com/windows-hardware/drivers/usbcon/).

### <a href="" id="sending-a-urb-to-a-pipe"></a> Sending an URB to a Pipe

If your KMDF driver communicates with a USB pipe by sending I/O requests that contain URBs, the driver can call the following methods:

<a href="" id="---------wdfusbtargetpipesendurbsynchronously--kmdf-only-"></a>[**WdfUsbTargetPipeSendUrbSynchronously (KMDF only)**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipesendurbsynchronously)  
Synchronously sends an I/O request that contains a URB.

<a href="" id="---------wdfusbtargetpipeformatrequestforurb--kmdf-only-"></a>[**WdfUsbTargetPipeFormatRequestForUrb (KMDF only)**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforurb)  
Formats an I/O request that contains a URB. The driver can call [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestsend) to send the request synchronously or asynchronously.

<a href="" id="---------wdfusbtargetpipewdmgetpipehandle--kmdf-only-"></a>[**WdfUsbTargetPipeWdmGetPipeHandle (KMDF only)**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetpipewdmgetpipehandle)  
Returns a device's USBD pipe handle. Some URBs require this handle.

 

 





