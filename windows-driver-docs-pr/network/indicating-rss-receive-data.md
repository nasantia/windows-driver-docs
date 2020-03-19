---
title: Indicating RSS Receive Data
description: Indicating RSS Receive Data
ms.assetid: 8d040d7d-3a8a-4d81-8508-8de225e000ab
keywords:
- receive-side scaling WDK networking , indicating receive data
- RSS WDK networking , indicating receive data
- indicating receive data WDK RSS
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Indicating RSS Receive Data





A miniport driver indicates received data by calling the [**NdisMIndicateReceiveNetBufferLists**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismindicatereceivenetbufferlists) function from its [*MiniportInterruptDPC*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_interrupt_dpc) function.

After the NIC computes the RSS hash value successfully, the driver should store the hash type, hashing function, and hash value in the [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structure with the following macros:

[**NET\_BUFFER\_LIST\_SET\_HASH\_TYPE**](https://docs.microsoft.com/windows-hardware/drivers/network/net-buffer-list-set-hash-type)

[**NET\_BUFFER\_LIST\_SET\_HASH\_FUNCTION**](https://docs.microsoft.com/windows-hardware/drivers/network/net-buffer-list-set-hash-function)

[**NET\_BUFFER\_LIST\_SET\_HASH\_VALUE**](https://docs.microsoft.com/windows-hardware/drivers/network/net-buffer-list-set-hash-value)

The hash type identifies the area of the received packet that the hash should be calculated over. For more information about the hash type, see [RSS Hashing Types](rss-hashing-types.md). The hashing function identifies the function that is used to calculate the hash value. For more information about hashing functions, see [RSS Hashing Functions](rss-hashing-functions.md). The protocol driver selects the hash type and function at initialization. For more information, see [RSS Configuration](rss-configuration.md).

If the NIC fails to identify the area of the packet that the hash type specifies, then it should not do any hash computation or scaling. In this case, the miniport driver or NIC should assign the received data to the default CPU.

If the NIC runs out of receive buffers, each buffer must be returned as soon as the original receive DPC returns. The miniport driver can indicate the received data with a status of NDIS\_STATUS\_RESOURCES. In this case, the overlying driver has to go through a slow path of copying the buffer descriptors and relinquishing ownership of the original one immediately.

For more information about receiving network data, see [Receiving Network Data](receiving-network-data.md).

 

 





