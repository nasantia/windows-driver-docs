---
title: Reporting a NIC's LSOV1 TCP-Packet-Segmentation Capabilities
description: Reporting a NIC's LSOV1 TCP-Packet-Segmentation Capabilities
ms.assetid: 976f5943-a50e-413b-8520-e280b04122f9
keywords:
- LSOV1 WDK networking
- large TCP packet segmentation WDK networking
- segmentation of large TCP packets WDK networking
- task offload WDK TCP/IP transport , LSOV1 and LSOV2
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Reporting a NIC's LSOV1 TCP-Packet-Segmentation Capabilities





An NDIS miniport driver specifies the current large send offload version 1 (LSOV1)-TCP-packet-segmentation configuration of a NIC in an [**NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V1**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_large_send_offload_v1) structure.Miniport drivers must include the current LSOV1 offload configuration in the [**NDIS\_MINIPORT\_ADAPTER\_OFFLOAD\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_miniport_adapter_offload_attributes) structure. Miniport drivers call the [**NdisMSetMiniportAttributes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsetminiportattributes) function from the [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) function and pass in the information in NDIS\_MINIPORT\_ADAPTER\_OFFLOAD\_ATTRIBUTES.

Miniport drivers must report changes in the LSOV1 configuration, if any, in the [**NDIS\_STATUS\_TASK\_OFFLOAD\_CURRENT\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-task-offload-current-config) status indication.

In response to a query of [OID\_TCP\_OFFLOAD\_CURRENT\_CONFIG](https://docs.microsoft.com/windows-hardware/drivers/network/oid-tcp-offload-current-config), NDIS includes the NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V1 structure in the [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure that NDIS returns in the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure. NDIS uses the information that the miniport driver provided.

NDIS supports large send offload version 2 (LSOV2), which is an enhanced version of LSO. For more information about LSOV2 capabilities, see [Reporting a NIC's LSOV2 TCP-Packet-Segmentation Capabilities](reporting-a-nic-s-lsov2-tcp-packet-segmentation-capabilities.md).

The miniport driver must specify the following information in the NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V1 structure:

-   Encapsulation settings, in the **Encapsulation** member. For more information about this member, see the Remarks section in [**NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V1**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_large_send_offload_v1).

-   The maximum bytes of user data that the TCP/IP transport can pass to the miniport driver in a large TCP packet, in the **MaxOffLoadSize** member. The maximum size cannot exceed 64K bytes.

-   The minimum number of segments that a large TCP packet must be divisible by before the TCP/IP transport can offload it to a NIC for segmentation, in the **MinSegmentCount** member.

-   Whether a NIC can segment a large TCP packet that contains TCP options.

-   Whether a NIC can segment a large TCP packet that contains IPv4 options.

## Related topics


[Determining Task Offload Capabilities](determining-task-offload-capabilities.md)

 

 






