---
title: USBCAMD2 Minidriver Operation
description: USBCAMD2 Minidriver Operation
ms.assetid: 395612cd-3407-4b42-b3a5-0afa838e73d9
keywords:
- Windows 2000 Kernel Streaming Model WDK , USBCAMD2 minidriver library
- Streaming Model WDK Windows 2000 Kernel , USBCAMD2 minidriver library
- Kernel Streaming Model WDK , USBCAMD2 minidriver library
- USBCAMD2 minidriver operations WDK Windows 2000 Kernel Streaming
- USB-based streaming cameras WDK USBCAMD2
- cameras WDK USBCAMD2
- SRBs WDK USBCAMD2
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# USBCAMD2 Minidriver Operation

A USBCAMD2 camera minidriver generally operates as follows:

- The camera minidriver calls [**USBCAMD\_DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_driverentry) from its [**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize) routine. When the minidriver calls **USBCAMD\_DriverEntry**, it passes to USBCAMD2 the minidriver's [**AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-padapter_receive_packet_routine) callback function. USBCAMD2 then registers the minidriver with the *stream.sys* class driver.

- The camera minidriver can then receive various stream request blocks (SRBs) in its *AdapterReceivePacket* callback function to handle, including:
  - [**SRB\_INITIALIZE\_DEVICE**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-initialize-device)
  - [**SRB\_INITIALIZATION\_COMPLETE**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-initialization-complete)
  - [**SRB\_GET\_STREAM\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-get-stream-info)
  - [**SRB\_GET\_DEVICE\_PROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-get-device-property)
  - [**SRB\_SET\_DEVICE\_PROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-set-device-property)
  - [**SRB\_GET\_DATA\_INTERSECTION**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-get-data-intersection)
  - [**SRB\_OPEN\_STREAM**](https://docs.microsoft.com/windows-hardware/drivers/stream/srb-open-stream)
- The camera minidriver determines how it must process each SRB. The minidriver can call routines in the USBCAMD2 minidriver library to assist with processing SRBs. These routines typically begin with the *USBCAMD\_* prefix.

For example, to specify the camera minidriver's other callback functions with USBCAMD2, the camera minidriver specifies their entry points in a [**USBCAMD\_DEVICE\_DATA2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/ns-usbcamdi-_usbcamd_device_data2) structure. The minidriver then calls [**USBCAMD\_InitializeNewInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_initializenewinterface) to pass the initialized USBCAMD\_DEVICE\_DATA2 structure to USBCAMD2. USBCAMD2 then calls the minidriver's callback functions when necessary.

> [!NOTE]
> The [**USBCAMD\_DEVICE\_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/ns-usbcamdi-_usbcamd_device_data) structure is supported in USBCAMD2 only for purposes of backward compatibility.

The minidriver must call [**USBCAMD\_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket) to send any SRBs it does not handle to USBCAMD2 to process.

[**USBCAMD Library Callback Functions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/index#callback-functions) describe the callback functions that the minidriver implements and whether they are optional or required.

The following list of procedures illustrates the general flow of processing for SRBs sent to the camera minidriver:

## Minidriver's SRB\_INITIALIZE\_DEVICE handler

| Component | Action |
| --- | --- |
| Camera minidriver | Initialize USBCAMD2 by calling [**USBCAMD_InitializeNewInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_initializenewinterface), indicating video or still raw processing requirements in kernel mode, such as enabling device events. |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Acquire USB device and configuration descriptors. |
| USBCAMD2 | Call the minidriver's [**CamConfigureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_configure_routine_ex) callback function. |
| Camera minidriver | Complete the configuration. Choose an alternate setting and maximum transfer size. Fill in the array of [**USBCAMD_Pipe_Config_Descriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/ns-usbcamdi-_pipe_config_descriptor) structures. |
| USBCAMD2 | Parse the array of **USBCAMD_Pipe_Config_Descriptor** structures. |
| USBCAMD2 | Call the minidriver's [**CamInitialize**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_initialize_routine) callback function. |
| Camera minidriver | Complete the initialization. Set the device power and activate the default setting on the camera. |
| USBCAMD2 | Provide the number of streams and stream descriptor size to the **stream.sys** class driver. |

## Minidriver's SRB\_GET\_STREAM\_INFO handler

| Component | Action |
| --- | --- |
| Camera minidriver | Provide the [**HW_STREAM_INFORMATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_information) stream information structure to the **stream.sys** class driver. |
| Camera minidriver | Fill in the pointer to the array of device property sets in **stream.sys** class driver's [**HW_STREAM_HEADER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_header) structure. |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Fill in the number of pins in the stream header. |
| USBCAMD2 | Expose the device event table, if any. |
| USBCAMD2 | Fix entry values in the stream information table. Set category name (capture or still). |
| USBCAMD2 | Fill in the pointer to the stream property array. |

## Minidriver's SRB\_INITIALIZATION\_COMPLETE handler

| Component | Action |
| --- | --- |
| Camera minidriver | Acquire GUID_USBCAMD_INTERFACE for USBCAMD2 using IRP_MJ_PNP and IRP_MN_QUERY_INTERFACE. |

## Minidriver's SRB\_GET\_DEVICE\_PROPERTY handler

| Component | Action |
| --- | --- |
| Camera minidriver | Get the properties that the camera minidriver handles, such as [**PROPSETID_VIDCAP_VIDEOPROCAMP**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-videoprocamp), [**PROPSETID_VIDCAP_CAMERACONTROL**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-cameracontrol), and [**PROPSETID_VIDCAP_VIDEOCONTROL**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-videocontrol), as well as any other custom property sets. |

## Minidriver's SRB\_SET\_DEVICE\_PROPERTY handler

| Component | Action |
| --- | --- |
| Camera minidriver | Set the properties the camera minidriver handles by acquiring the parameters of [**PROPSETID_VIDCAP_VIDEOPROCAMP**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-videoprocamp), [**PROPSETID_VIDCAP_CAMERACONTROL**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-cameracontrol), and [**PROPSETID_VIDCAP_VIDEOCONTROL**](https://docs.microsoft.com/windows-hardware/drivers/stream/propsetid-vidcap-videocontrol), and any other custom property sets. |

## Minidriver's SRB\_GET\_DATA\_INTERSECTION handler

| Component | Action |
| --- | --- |
| Camera minidriver | Return a [**KSDATAFORMAT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksdataformat) structure from a [**KSDATARANGE**](https://docs.microsoft.com/previous-versions/ff561658(v=vs.85)) structure. |
| Camera minidriver | Check that the frame rate requested (**VideoInfoHeader.AvgTimePerFrame**) is within the upper and lower limits for the video format requested. If it exceeds the limits, the minidriver should correct the following values in pSrb->CommandData.IntersectInfo->Datarange: VideoInfoHeader.AvgTimePerFrame, VideoInfoHeader.dwBitRate. |

## Minidriver's SRB\_OPEN\_STREAM handler

| Component | Action |
| --- | --- |
| Camera minidriver | Verify the video format. |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Save the video format accepted by the camera minidriver. |
| USBCAMD2 | Call the minidriver's [**CamAllocateBandwidthEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_allocate_bw_routine_ex) callback function to allocate bandwidth based on video-format data and get the maximum buffer size for the video format. |
| Camera minidriver | Calculate the isochronous channel's maximum packet size that satisfies the requested frame rate and output windows size. |
| Camera minidriver | Choose the closest alternate setting by calling [**USBCAMD_SelectAlternateInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_selectalternateinterface). The minidriver should provide USBCAMD2 with the maximum possible frame size that can be produced by the camera. |
| Camera minidriver | Set the hardware scaling on the camera. Set the camera controls to the stored values in the registry, or to the default setting if the first time. |
| Camera minidriver | Ensure that the frame rate (VideoInfoHeader.AvgTimePerFrame) falls within the limits for the video format, and correct it if it does not. |
| USBCAMD2 | Call the minidriver's [**CamStartCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_start_capture_routine_ex) callback function. |
| Camera minidriver | Set the hardware to capture mode. |
| USBCAMD2 | Initialize isochronous or bulk transfer. |

## Minidriver's SRB\_CLOSE\_STREAM handler

| Component | Action |
| --- | --- |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Cancel pending IRPs submitted to USBCAMD2. Return any pending data SRBs to the **stream.sys** class driver. |
| USBCAMD2 | Call the minidriver's [**CamStopCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_stop_capture_routine_ex) callback function. |
| Camera minidriver | Send a stop-capture command to the camera. |
| USBCAMD2 | Call the minidriver's [**CamFreeBandwidthEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_free_bw_routine_ex) callback function to free isochronous bus bandwidth, if applicable. |
| Camera minidriver | Select an idle alternate setting. |
| USBCAMD2 | Free resources associated with USB pipes. |

## Minidriver's SRB\_UNINITIALIZE\_DEVICE handler

| Component | Action |
| --- | --- |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | If any streams are still open, close them by calling the minidriver's [**CamStopCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_stop_capture_routine_ex) and [**CamFreeBandwidthEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_free_bw_routine_ex) callback functions for each stream. |
| USBCAMD2 | Call the minidriver's [**CamUnInitialize**](https://docs.microsoft.com/previous-versions/ff557646(v=vs.85)) callback function. |
| Camera minidriver | Clean up and free resources. |

## Minidriver's SRB\_SURPRISE\_REMOVAL handler

| Component | Action |
| --- | --- |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Cancel pending data SRBs and return the SRBs with STATUS_CANCELLED. |
| USBCAMD2 | Call the minidriver's [**CamStopCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_stop_capture_routine_ex) and [**CamFreeBandwidthEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_free_bw_routine_ex) callback functions on all opened streams. |
| USBCAMD2 | Return STATUS_CANCELLED on any read/write SRBs that come down after SRB_SURPRISE_REMOVAL. |

## Minidriver's SRB\_SET\_DATA\_FORMAT handler

| Component | Action |
| --- | --- |
| Camera minidriver | Verify the new video format. |
| Camera minidriver | Call [**USBCAMD_SetVideoFormat**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pfnusbcamd_setvideoformat). |
| USBCAMD2 | Save the new format with the associated stream extension. |

## Minidriver's SRB\_CHANGE\_POWER\_STATE from Power ON to Power OFF handler

| Component | Action |
| --- | --- |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Stop streaming on isochronous pipe if applicable, or cancel pending bulk or interrupt transfers. |
| USBCAMD2 | Call the minidriver's [**CamStopCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_stop_capture_routine_ex) callback function. |
| Camera minidriver | Send stop capture command to hardware. |

## Minidriver's SRB\_CHANGE\_POWER\_STATE from Power OFF to Power ON handler

| Component | Action |
| --- | --- |
| Camera minidriver | Call [**USBCAMD_AdapterReceivePacket**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nf-usbcamdi-usbcamd_adapterreceivepacket). |
| USBCAMD2 | Restart streaming on isochronous pipe if applicable, or resubmit bulk or interrupt transfer to USB class. |
| Camera minidriver | Restore camera settings and camera power consumption to normal levels. |
| USBCAMD2 | Call the minidriver's [**CamStopCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_stop_capture_routine_ex) callback function. |
| USBCAMD2 | Call the minidriver's [**CamStartCaptureEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbcamdi/nc-usbcamdi-pcam_start_capture_routine_ex) callback function. |
