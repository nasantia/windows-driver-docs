---
title: Miniport Driver Buffer Management
description: Miniport Driver Buffer Management
ms.assetid: 3b8844e0-9b38-4030-9aec-b713643de523
keywords:
- buffers WDK NDIS miniport
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Miniport Driver Buffer Management





Miniport drivers typically call [**NdisAllocateNetBufferListPool**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistpool) from [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) to create a pool of [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structures. Miniport drivers use these structures to indicate received data.

Typically, a miniport driver that allocates a NET\_BUFFER\_LIST structure will allocate and queue one [**NET\_BUFFER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) structure on that NET\_BUFFER\_LIST structure. It is more efficient to preallocate NET\_BUFFER structures when you allocate a pool of NET\_BUFFER\_LIST structures than to allocate NET\_BUFFER\_LIST structures and NET\_BUFFER structures separately.

Miniport drivers can call **NdisAllocateNetBufferListPool** and set the *AllocateNetBuffer* parameter to **TRUE** to indicate that [**NET\_BUFFER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) structures are preallocated. In this case, a NET\_BUFFER structure is preallocated with each NET\_BUFFER\_LIST structure that the driver allocates from the pool. Such drivers must call [**NdisAllocateNetBufferAndNetBufferList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferandnetbufferlist) to allocate structures from this pool.

Typically, a miniport driver calls **NdisAllocateNetBufferAndNetBufferList** from *MiniportInitializeEx* to allocate as many buffers as it will require for subsequent receive operations. In this case, the driver manages an internal list of free buffers.

The [*MiniportReturnNetBufferLists*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_return_net_buffer_lists) function can prepare a returned NET\_BUFFER\_LIST structure for reuse in a subsequent receive indication. Although *MiniportReturnNetBufferLists* could return the NET\_BUFFER\_LIST structures to a pool (for example, it could call [**NdisFreeNetBufferList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlist)), it can be more efficient to reuse the structures without returning them to the pool.

A miniport driver should free all the NET\_BUFFER\_LIST structures and associated data when NDIS halts the adapter. A driver can call **NdisFreeNetBufferList** to free the structures and the [**NdisFreeNetBufferListPool**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistpool) function to free the NET\_BUFFER\_LIST pool.

 

 





