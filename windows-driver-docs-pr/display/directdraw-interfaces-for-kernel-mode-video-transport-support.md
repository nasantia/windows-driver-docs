---
title: DirectDraw Interfaces for Kernel-Mode Video Transport
description: DirectDraw Interfaces for Kernel-Mode Video Transport Support
ms.assetid: 8012f6b0-3b55-438f-8146-4f62e6bafad3
keywords:
- kernel-mode video transport WDK DirectDraw , interfaces
- DirectX VPE support WDK DirectDraw , kernel-mode video transport
- drawing VPEs WDK DirectDraw , kernel-mode video transport
- DirectDraw VPEs WDK Windows 2000 display , kernel-mode video transport
- video port extensions WDK DirectDraw , kernel-mode video transport
- VPEs WDK DirectDraw , kernel-mode video transport
ms.date: 12/06/2018
ms.localizationpriority: medium
ms.custom: seodec18
---

# DirectDraw Interfaces for Kernel-Mode Video Transport Support

The kernel-mode video transport must keep track of surface information for each surface it uses, and for each VPE object. This information must be updated every time [*DdUpdateOverlay*](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_surfcb_updateoverlay) or [*DdVideoPortUpdate*](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_vportcb_update) is called for the surface or hardware video port. Before DirectDraw sends this information to the kernel-mode video transport, it calls one of two driver functions: [*DdSyncSurfaceData*](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_kernelcb_syncsurface) or [*DdSyncVideoPortData*](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_kernelcb_syncvideoport). These functions allow the driver to fill in or modify some of the structure information and to use four **dwDriverReserved**_N_ members of the [**DD\_SYNCSURFACEDATA**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-_dd_syncsurfacedata) or three **dwDriverReserved**_N_ members of the [**DD\_SYNCVIDEOPORTDATA**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-_dd_syncvideoportdata) structure for its own purposes. These driver functions are required for the kernel-mode video transport support to work correctly.

A good example of how a driver can use these **dwDriverReserved**_N_ members is to set a flag indicating which physical overlay an overlay surface is using if the hardware supports more than one physical overlay.

 

 





