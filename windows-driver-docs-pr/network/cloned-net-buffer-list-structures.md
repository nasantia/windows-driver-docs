---
title: Cloned NET_BUFFER_LIST Structures
description: Cloned NET_BUFFER_LIST Structures
ms.assetid: efcf7d03-401e-46da-9ca3-8423af1e385a
keywords:
- NET_BUFFER_LIST
- cloned structures WDK networking
- duplicate structures WDK networking
- parent/child NET_BUFFER_LIST relationships WDK networking
- child/parent NET_BUFFER_LIST relationships WDK networking
- relationships WDK NET_BUFFER_LIST
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Cloned NET\_BUFFER\_LIST Structures





An NDIS driver creates a cloned [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structure from an existing NET\_BUFFER\_LIST structure. The cloned structure references the original structures data. Drivers can use this type of structure to efficiently transfer the same data to multiple paths.

The following figure shows the relationship between a parent NET\_BUFFER\_LIST structure and a cloned child structure.

![diagram illustrating the relationship between a parent net\-buffer\-list structure and a cloned child structure](images/netbufferlistclone.png)

The preceding figure contains a parent [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structure and a child structure that was derived from that parent. The parent structure has one [**NET\_BUFFER\_LIST\_CONTEXT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list_context) structure and one [**NET\_BUFFER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) structure with MDLs attached. The parent structure's parent pointer is **NULL** indicating that it is not a derived structure.

The child NET\_BUFFER\_LIST structure has one NET\_BUFFER structure with MDLs attached. The child NET\_BUFFER\_LIST has a pointer to the parent structure. The **NULL** where a NET\_BUFFER\_LIST\_CONTEXT structure pointer would be indicates that the child has no NET\_BUFFER\_LIST\_CONTEXT structure.

Drivers call the [**NdisAllocateCloneNetBufferList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocateclonenetbufferlist) function to create a clone [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structure. NDIS allocates new [**NET\_BUFFER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) structures and MDLs with the cloned NET\_BUFFER\_LIST structure. NDIS does not allocate a [**NET\_BUFFER\_LIST\_CONTEXT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list_context) structure for the cloned structure. The new NET\_BUFFER structures and MDLs describe the same data as in the parent structure. The data is not copied.

Drivers call the [**NdisFreeCloneNetBufferList**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreeclonenetbufferlist) function to free a NET\_BUFFER\_LIST structure and all associated NET\_BUFFER structures and MDL chains that were previously allocated by calling **NdisAllocateCloneNetBufferList**.

## Related topics


[Derived NET\_BUFFER\_LIST Structures](derived-net-buffer-list-structures.md)

 

 






