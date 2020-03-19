---
title: Obtaining Pool Handles
description: Obtaining Pool Handles
ms.assetid: 752b0d64-2ca3-4dc0-a6cd-642e96af1f8f
keywords:
- pool handles WDK networking
- protocol drivers WDK networking , pool handles
- NDIS protocol drivers WDK , pool handles
- miniport drivers WDK networking , pool handles
- NDIS miniport drivers WDK , pool handles
- intermediate drivers WDK networking , po
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Obtaining Pool Handles





The following NDIS pool allocation functions require a handle to allocate resources:

-   [**NdisAllocateNetBufferPool**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferpool)

-   [**NdisAllocateNetBufferListPool**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistpool)

NDIS 6.0 drivers obtain a handle as follows:

<a href="" id="protocol-drivers"></a>Protocol drivers  
Protocol drivers call the [**NdisRegisterProtocolDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisregisterprotocoldriver) function to obtain a handle.

<a href="" id="miniport-drivers"></a>Miniport drivers  
NDIS calls the [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) function to pass the handle to the miniport driver.

<a href="" id="intermediate-drivers"></a>Intermediate drivers  
Intermediate drivers call the [**NdisRegisterProtocolDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisregisterprotocoldriver) function to obtain a handle for pools used in send operations and NDIS calls *MiniportInitializeEx* to pass the handle to the intermediate driver for pools used in receive operations.

<a href="" id="filter-drivers"></a>Filter drivers  
NDIS calls the [*FilterAttach*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_attach) function to pass the handle to the filter driver.

<a href="" id="other-drivers"></a>Other drivers  
If a driver cannot obtain a handle through one of the preceding methods, the driver can call the [**NdisAllocateGenericObject**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocategenericobject) function to get a handle.

 

 





