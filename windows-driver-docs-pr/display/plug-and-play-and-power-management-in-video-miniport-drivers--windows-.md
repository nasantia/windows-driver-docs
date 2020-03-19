---
title: Power Management and PnP in Video Miniport Drivers (XDDM)
description: Power Management and Plug and Play in Video Miniport Drivers (Windows 2000 Model)
ms.assetid: e5b2ac53-e492-43de-91a3-5b02c26ee9a3
keywords:
- video miniport drivers WDK Windows 2000 , Plug and Play
- video miniport drivers WDK Windows 2000 , power management
- Plug and Play WDK video miniport
- PnP WDK video miniport
- power management WDK video miniport
ms.date: 12/06/2018
ms.localizationpriority: medium
ms.custom: seodec18
---

# Power Management and Plug and Play in Video Miniport Drivers (Windows 2000 Model)


## <span id="ddk_plug_and_play_and_power_management_in_video_miniport_drivers_windo"></span><span id="DDK_PLUG_AND_PLAY_AND_POWER_MANAGEMENT_IN_VIDEO_MINIPORT_DRIVERS_WINDO"></span>


All Windows 2000 and later miniport drivers must support Plug and Play and Power Management. This includes the ability to enumerate child devices such as *DDC* monitors, inter-integrated circuit (I²C) devices, and secondary adapters.

The video port driver manages most of the PnP requirements for the miniport driver, including creating the FDO (Functional Device Object) and receiving and dispatching PnP-specific IRP codes (see [IRP Major Function Codes](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-major-function-codes)) on the miniport driver's behalf.

Miniport drivers must implement the following functions to support PnP and Power Management:

[*HwVidSetPowerState*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_power_set)

[*HwVidGetPowerState*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_power_get)

[*HwVidGetVideoChildDescriptor*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_get_child_descriptor)

The graphics adapter for a legacy miniport driver cannot be removed from the system while the system is running, nor are legacy miniport drivers automatically detected when added to a running system.

See [Child Devices of the Display Adapter (Windows 2000 Model)](child-devices-of-the-display-adapter--windows-2000-model-.md) for more information about detecting and communicating with an adapter's child devices. For general information about Plug and Play drivers, see [Plug and Play](https://docs.microsoft.com/windows-hardware/drivers/kernel/implementing-plug-and-play).

 

 





