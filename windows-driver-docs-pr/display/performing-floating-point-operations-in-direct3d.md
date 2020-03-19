---
title: Performing Floating-point Operations in Direct3D
description: Performing Floating-point Operations in Direct3D
ms.assetid: 2da736cf-d062-4c5a-b9f5-6b35f199660f
keywords:
- floating-point operations WDK Direct3D
- Direct3D WDK Windows 2000 display , floating-point operations
- callback functions WDK Direct3D
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Performing Floating-point Operations in Direct3D


## <span id="ddk_performing_floating_point_operations_in_direct3d_gg"></span><span id="DDK_PERFORMING_FLOATING_POINT_OPERATIONS_IN_DIRECT3D_GG"></span>


The DirectX runtime saves and restores floating-point state when it calls many of a display driver's Direct3D callback functions. However, as described in [Performing Floating-point Operations in DirectDraw](performing-floating-point-operations-in-directdraw.md), some of the driver's Direct3D callback functions must save floating-point state prior to performing floating-point operations and must restore floating-point state when the operations complete.

The DirectX runtime saves and restores floating-point state as required for the following Direct3D callback functions:

-   [**D3dContextCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/nc-d3dhal-lpd3dhal_contextcreatecb)

-   [**D3dContextDestroy**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/nc-d3dhal-lpd3dhal_contextdestroycb)

-   [**D3dDrawPrimitives2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/nc-d3dhal-lpd3dhal_drawprimitives2cb)

-   [**D3dGetDriverState**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_getdriverstate)

-   [**D3dValidateTextureStageState**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/nc-d3dhal-lpd3dhal_validatetexturestagestatecb)

For the following callback functions, a Direct3D-supported display driver must save floating-point state before performing floating-point operations, and restore it when the operations are complete:

-   [**D3dCreateSurfaceEx**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_createsurfaceex)

-   [**D3dDestroyDDLocal**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_destroyddlocal)

-   [D3DBuffer Callbacks](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)

For more information about floating-point operations, see [Floating-Point Operations in Graphics Driver Functions](floating-point-operations-in-graphics-driver-functions.md).

 

 





