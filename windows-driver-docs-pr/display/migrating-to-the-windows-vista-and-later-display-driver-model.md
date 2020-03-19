---
title: Migrating to the Windows Display Driver Model (WDDM)
description: Migrating to the Windows Display Driver Model (WDDM)
ms.assetid: 7f926aa7-1698-4a4e-a1ce-54a316bdc0cd
keywords:
- display driver model WDK Windows Vista , migrating
- Windows Vista display driver model WDK , migrating
- migrating display driver model WDK Windows Vista
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Migrating to the Windows Display Driver Model (WDDM)


## <span id="ddk_migrating_to_the_longhorn_display_driver_model_gg"></span><span id="DDK_MIGRATING_TO_THE_LONGHORN_DISPLAY_DRIVER_MODEL_GG"></span>


Migrating to the Windows Display Driver Model (WDDM)) requires driver writers to write completely different display and video miniport drivers. Similar to the [Windows 2000 display driver model (XDDM)](windows-2000-display-driver-model-design-guide.md), WDDM requires a paired display driver and display miniport driver. However, in WDDM, the display driver runs in user mode. Also, the model does not use services of the Windows Graphics Device Interface (GDI) engine; the model uses services of the Microsoft Direct3D runtime and Microsoft DirectX graphics kernel subsystem (Dxgkrnl.sys).

WDDM supports display and video miniport drivers written according to XDDM. However, new drivers should be written as WDDM drivers, whenever possible, to take advantage of software and hardware features available starting with Windows Vista.

Although driver writers can reuse low-level hardware-dependent code in their WDDM drivers, they should rewrite new device driver interface (DDI)-related code. When writing WDDMdrivers, consider these points:

-   The display miniport driver must implement a revised set of entry-point functions to interact with the operating system and the DirectX graphics kernel subsystem. For more information, see [**DriverEntry of Display Miniport Driver**](https://docs.microsoft.com/windows-hardware/drivers/display/driverentry-of-display-miniport-driver). The display miniport driver can call any documented kernel function.

-   The display miniport driver dynamically loads the appropriate DirectX graphics kernel subsystem. The display miniport driver and the DirectX graphics kernel subsystem call each other through interfaces.

-   The display miniport driver is no longer required to process most video I/O control codes (IOCTL). In XDDM, the kernel-mode display driver uses these codes to communicate with the video miniport driver. In WDDM, the user-mode display driver communicates with the Direct3D runtime; the WDDM graphics kernel subsystem, in turn, communicates with the display miniport driver.
    **Note**   The following IOCTLs are still used in WDDM, and the display miniport driver must process them:
    [**IOCTL\_VIDEO\_QUERY\_COLOR\_CAPABILITIES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddvdeo/ni-ntddvdeo-ioctl_video_query_color_capabilities)
    [**IOCTL\_VIDEO\_HANDLE\_VIDEOPARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddvdeo/ni-ntddvdeo-ioctl_video_handle_videoparameters)

     

<!-- -->

-   The user-mode display driver must implement and export an [**OpenAdapter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_openadapter) function, which opens an instance of the graphics adapter. The user-mode display driver must also implement a [**CreateDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_createdevice) function, which creates representations of display devices that handle collections of rendering state.

-   The user-mode display driver's [**CreateResource**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_createresource) function, along with the display miniport driver's [**DxgkDdiCreateAllocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_createallocation) function, replace the [*DdCanCreateSurface*](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff549213(v=vs.85)), [*DdCreateSurface*](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff549263(v=vs.85)), and [**D3dCreateSurfaceEx**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_createsurfaceex) functions in XDDM.

-   Most of the remaining user-mode display driver functions implement the same functionality that the kernel-mode display driver for XDDM implemented in the following:
    -   The [**D3dDrawPrimitives2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/nc-d3dhal-lpd3dhal_drawprimitives2cb) function and [**DP2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/ne-d3dhal-_d3dhal_dp2operation) operation codes
    -   The [motion compensation callback functions](https://docs.microsoft.com/windows-hardware/drivers/ddi/index) and [DirectX Video Acceleration structures](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)

 

 





