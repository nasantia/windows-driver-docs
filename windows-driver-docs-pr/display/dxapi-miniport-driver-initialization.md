---
title: DxApi Miniport Driver Initialization
description: DxApi Miniport Driver Initialization
ms.assetid: 8d2bb81c-618e-43e0-9a1a-ff0ceb732d90
keywords:
- DxApi miniport drivers WDK DirectDraw , initializing
- initializing DxApi miniport drivers
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# DxApi Miniport Driver Initialization


## <span id="ddk_dxapi_miniport_driver_initialization_gg"></span><span id="DDK_DXAPI_MINIPORT_DRIVER_INITIALIZATION_GG"></span>


To enable DxApi interface functionality, the DirectDraw driver must perform the following tasks at initialization time:

1.  The driver must specify a [**DdGetDriverInfo**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_getdriverinfo) function in the [**DD\_HALINFO**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-_dd_halinfo) structure that DirectDraw can call to get additional information.

2.  The *DdGetDriverInfo* callback is called with the GUID\_KernelCallbacks GUID specified. The driver must fill in a [**DD\_KERNELCALLBACKS**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-dd_kernelcallbacks) structure with the appropriate callbacks and flags set. The driver then copies this structure to the **lpvData** member of the [**DD\_GETDRIVERINFODATA**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-_dd_getdriverinfodata) structure.

3.  The *DdGetDriverInfo* callback is called with GUID\_KernelCaps GUID specified. The driver must fill in a [**DDKERNELCAPS**](https://docs.microsoft.com/windows/desktop/api/ddkernel/ns-ddkernel-_ddkernelcaps) structure. The driver then copies this structure to the **lpvData** member of the DD\_GETDRIVERINFODATA structure.

4.  The DirectDraw runtime calls the video port driver IOCTL handler with **MajorFunction** = IRP\_MJ\_PNP, **MinorFunction** = IRP\_MN\_QUERY\_INTERFACE, and **InterfaceType** = GUID\_DxApi. The video port driver then calls the video miniport driver's [*HwVidQueryInterface*](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_query_interface) function to fill in the [**DXAPI\_INTERFACE**](https://docs.microsoft.com/windows/desktop/api/dxmini/ns-dxmini-_dxapi_interface) structure with pointers to the DxApi interface callback functions that DirectDraw can call. These callback functions are listed in [Kernel-Mode Video Transport Callback Functions](kernel-mode-video-transport-callback-functions.md).

The video miniport driver can specify a value in the **Context** member of the [**DXAPI\_INTERFACE**](https://docs.microsoft.com/windows/desktop/api/dxmini/ns-dxmini-_dxapi_interface) structure that is passed to the video miniport driver each time one of these functions is called.

 

 





