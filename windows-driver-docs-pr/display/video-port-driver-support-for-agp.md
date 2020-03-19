---
title: Video Port Driver Support for AGP
description: Video Port Driver Support for AGP
ms.assetid: 445dbe4a-7f7b-4dcc-9891-17fd8fb03a6c
keywords:
- video miniport drivers WDK Windows 2000 , AGP
- AGP WDK video miniport
- memory WDK video miniport
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Video Port Driver Support for AGP


## <span id="ddk_video_port_driver_support_for_agp_gg"></span><span id="DDK_VIDEO_PORT_DRIVER_SUPPORT_FOR_AGP_GG"></span>


The video port driver implements the following functions to support Accelerated Graphics Port (AGP).

[**AgpReservePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_physical)

[**AgpCommitPhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_physical)

[**AgpReserveVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_virtual)

[**AgpCommitVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_virtual)

[**AgpFreeVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_free_virtual)

[**AgpReleaseVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_release_virtual)

[**AgpFreePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_free_physical)

[**AgpReleasePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_release_physical)

[**AgpSetRate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_set_rate)

Before the video miniport driver calls the functions in the preceding list, it must obtain function pointers by calling [**VideoPortQueryServices**](https://docs.microsoft.com/windows-hardware/drivers/ddi/video/nf-video-videoportqueryservices). For more information about obtaining pointers to the AGP functions, see [AGP Functions Implemented by the Video Port Driver](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/).

The video miniport driver performs the following steps to reserve and commit a portion of the AGP aperture through which the display adapter can access system memory:

1.  Call [**AgpReservePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_physical) to reserve a contiguous range of physical addresses in the AGP aperture.

2.  Call [**AgpCommitPhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_physical) to map a portion (or all) of the address range returned by *AgpReservePhysical* to pages in system memory. The pages in system memory are locked, but not necessarily contiguous. The video miniport driver can call *AgpCommitPhysical* several times to do several small commitments rather than one large one. However, the driver must not attempt to commit a range that is already committed.

Then, for an application to be able to see and use the committed pages in system memory, the video miniport driver performs the following steps:

1.  Call [**AgpReserveVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_virtual) to reserve a range of virtual addresses in the application's address space. The video miniport driver must pass *AgpReserveVirtual* a handle, previously returned by *AgpReservePhysical*, so that the reserved virtual address range can be associated with the physical address range created by *AgpReservePhysical*.

2.  Call [**AgpCommitVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_virtual) to map a portion of the virtual address range returned by *AgpReserveVirtual* to pages in system memory. The pages that *AgpCommitVirtual* maps must have been previously mapped by a call to *AgpCommitPhysical*. Furthermore, that mapping established by *AgpCommitPhysical* must still be current; that is, those pages must not have been freed by a call to [**AgpFreePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_free_physical).

**Note**   Whenever you use the AGP functions to commit or reserve an address range (physical or virtual), the size of the range must be a multiple of 64 kilobytes.

 

The video miniport driver is responsible for releasing and freeing all memory that it has reserved and committed by calling the following functions:

-   [**AgpFreeVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_free_virtual) unmaps virtual addresses that were mapped to system memory by a prior call to [**AgpCommitVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_virtual).

-   [**AgpReleaseVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_release_virtual) releases virtual addresses that were reserved by a prior call to [**AgpReserveVirtual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_virtual).

-   [**AgpFreePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_free_physical) unmaps physical addresses that were mapped to system memory by a prior call to [**AgpCommitPhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_commit_physical).

-   [**AgpReleasePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_release_physical) releases physical addresses that were reserved by a prior call to [**AgpReservePhysical**](https://docs.microsoft.com/windows-hardware/drivers/ddi/videoagp/nc-videoagp-pagp_reserve_physical).

 

 





