---
title: Querying a Connection-Oriented Miniport Driver
description: Querying a Connection-Oriented Miniport Driver
ms.assetid: 9e9926f6-cf90-48af-885f-59725721948d
keywords:
- connection-oriented drivers WDK networking
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Querying a Connection-Oriented Miniport Driver





To query information objects that a connection-oriented miniport driver maintains, a bound protocol calls [**NdisCoOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscooidrequest) and passes an [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure that specifies the object (OID) that is being queried and that provides a buffer into which NDIS eventually writes the requested information. The call to **NdisCoOidRequest** causes NDIS to call the miniport driver's [*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) function, which returns the requested information to NDIS. *MiniportCoOidRequest* can complete synchronously or asynchronously with a call to [**NdisCoOidRequestComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscooidrequestcomplete).

NDIS can also call a miniport driver's [*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) function on its own behalf—for example, after the miniport driver's [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) function has returned NDIS\_STATUS\_SUCCESS—to query the miniport driver's capabilities, status, or statistics. The following diagram illustrates querying a connection-oriented miniport driver.

![diagram illustrating querying a connection-oriented miniport driver](images/fig5-3.png)

A connection-oriented miniport driver must be able to provide information about a global basis for all virtual connections (VCs) for a particular NIC and also on a per-VC basis. For example, if a non-**NULL** *NdisVcHandle* is supplied to [*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) for a query of [OID\_GEN\_CO\_RCV\_CRC\_ERROR](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-rcv-crc-error), the miniport driver returns the number of CRC errors that were encountered in all receives on the specified VC. For the same request with a **NULL** *NdisVcHandle*, the miniport driver returns the total number of CRC errors that are encountered for all incoming receives through a NIC.

The following list contains the set of mandatory general operational OIDs for connection-oriented miniport drivers:

[OID\_GEN\_CO\_SUPPORTED\_LIST](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-supported-list)

[OID\_GEN\_CO\_HARDWARE\_STATUS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-hardware-status)

[OID\_GEN\_CO\_MEDIA\_SUPPORTED](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-media-supported)

[OID\_GEN\_CO\_MEDIA\_IN\_USE](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-media-in-use)

[OID\_GEN\_CO\_LINK\_SPEED](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-link-speed)

[OID\_GEN\_CO\_VENDOR\_ID](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-vendor-id)

[OID\_GEN\_CO\_VENDOR\_DESCRIPTION](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-vendor-description)

[OID\_GEN\_CO\_VENDOR\_DRIVER\_VERSION](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-vendor-driver-version)

[OID\_GEN\_CO\_DRIVER\_VERSION](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-driver-version)

[OID\_GEN\_CO\_MAC\_OPTIONS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-mac-options)

[OID\_GEN\_CO\_MEDIA\_CONNECT\_STATUS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-media-connect-status)

[OID\_GEN\_CO\_MINIMUM\_LINK\_SPEED](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-co-minimum-link-speed)

The miniport driver's [*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) function must be prepared to respond to queries or sets, as appropriate, to any of the preceding OIDs.

When [*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) is called with OID\_GEN\_CO\_MAC\_OPTIONS, it must return a bitmask that specifies the optional operations that the miniport driver performs. The set of flags includes:

-   NDIS\_MAC\_OPTION\_NO\_LOOPBACK. If this flag is set, the miniport driver does not loopback a packet that is passed to [**MiniportCoSendNetBufferLists**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_send_net_buffer_lists) that is directed to a receiver on the same computer and that the miniport driver expects NDIS to perform the loopback. If NDIS performs the loopback of a packet, the packet is not passed down to the miniport driver. A miniport driver always sets this flag unless a NIC performs hardware loopbacks.

-   NDIS\_MAC\_ETOX\_INDICATION. If this flag is set, the miniport driver indicates that a send is complete only after the NIC transmits the packet.

A miniport driver must never use the NDIS\_MAC\_OPTION\_RESERVED flag, which is reserved for NDIS internal use.

[*MiniportCoOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) will also be queried with a media-specific OID to determine the NIC's current address.

For more information, see [OIDs for Connection-Oriented Call Managers and Clients](https://docs.microsoft.com/windows-hardware/drivers/network/oids-for-connection-oriented-call-managers-and-clients) and [General Objects](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff546510(v=vs.85)).

 

 





