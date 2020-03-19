---
title: Sending Data from a Miniport Driver
description: Sending Data from a Miniport Driver
ms.assetid: f82475ff-8d32-4448-9b19-b6fa97a93d32
keywords:
- sending data WDK networking
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Sending Data from a Miniport Driver





The following figure illustrates a miniport driver send operation.

![diagram illustrating a miniport driver send operation](images/miniportsend.png)

NDIS calls a miniport driver's [*MiniportSendNetBufferLists*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_send_net_buffer_lists) function to transmit the network data that is described by a linked list of [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structures.

Miniport drivers call the [**NdisMSendNetBufferListsComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsendnetbufferlistscomplete) function to return a linked list of NET\_BUFFER\_LIST structures to an overlying driver and to return the final status of a send request.

 

 





