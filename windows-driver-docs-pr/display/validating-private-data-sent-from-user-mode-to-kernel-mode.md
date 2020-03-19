---
title: Validating Private Data Sent from User Mode to Kernel Mode
description: Validating Private Data Sent from User Mode to Kernel Mode
ms.assetid: 7022af7b-80e7-41a5-bd53-32d7eafc4062
keywords:
- validating private data WDK display
- private data validation WDK display
- invalid private data WDK display
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Validating Private Data Sent from User Mode to Kernel Mode


A display miniport driver must validate all private data sent from the user-mode display driver to prevent the miniport driver from crashing, not responding (hanging), asserting, or corrupting memory if the private data is invalid. However, because the operating system resets hardware that "hangs," the display miniport driver can send instructions to the graphics processing unit (GPU) that cause the GPU to "hang." Private data can include any of the following items:

-   Command buffer content sent to the miniport driver's [**DxgkDdiRender**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_render) or [**DxgkDdiRenderKm**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_renderkm) function in the **pCommand** buffer member of the [**DXGKARG\_RENDER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_render) structure.

-   Data sent to the following miniport driver functions:
    -   The [**DxgkDdiCreateAllocation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_createallocation) function in the **pPrivateDriverData** buffer members of the [**DXGKARG\_CREATEALLOCATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_createallocation) and [**DXGK\_ALLOCATIONINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgk_allocationinfo) structures.
    -   The [**DxgkDdiEscape**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_escape) function in the **pPrivateDriverData** buffer member of the [**DXGKARG\_ESCAPE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_escape) structure.
    -   The [**DxgkDdiAcquireSwizzlingRange**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_acquireswizzlingrange) function in the **PrivateDriverData** 32-bit member of the [**DXGKARG\_ACQUIRESWIZZLINGRANGE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_acquireswizzlingrange) structure.
    -   The [**DxgkDdiReleaseSwizzlingRange**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_releaseswizzlingrange) function in the **PrivateDriverData** 32-bit member of the [**DXGKARG\_RELEASESWIZZLINGRANGE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_releaseswizzlingrange) structure.
    -   The [**DxgkDdiQueryAdapterInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_queryadapterinfo) function in the **pInputData** buffer member of the [**DXGKARG\_QUERYADAPTERINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_queryadapterinfo) structure when the DXGKQAITYPE\_UMDRIVERPRIVATE value is specified in the **Type** member.

 

 





