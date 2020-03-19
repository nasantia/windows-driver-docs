---
title: Determining Task Offload Capabilities
description: Determining Task Offload Capabilities
ms.assetid: 9348a595-7bc0-467e-aeaf-e23100c99524
keywords:
- task offload WDK TCP/IP transport , capabilities
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Determining Task Offload Capabilities





NDIS supports task offload services that are enhanced forms of the NDIS 5.1 and earlier task offload services. For more information about how to determine connection offload capabilities, see [Determining Connection Offload Capabilities](determining-connection-offload-capabilities.md).

NDIS provides the offload hardware capabilities and the current configuration of the underlying miniport adapter to protocol drivers in the [**NDIS\_BIND\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_bind_parameters) structure. NDIS provides the task offload hardware capabilities and current configuration of the underlying miniport adapter to filter drivers in the [**NDIS\_FILTER\_ATTACH\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_filter_attach_parameters) structure.

Administrative applications use object identifier (OID) queries to obtain task offload capabilities of a miniport adapter. However, overlying drivers should avoid using OID queries. Protocol drivers must handle changes in the task offload capabilities that underlying drivers report. Miniport drivers can report changes in task offload capabilities in status indications. For a list of status indications, see [NDIS 6.0 TCP/IP Offload Status Indications](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-tcp-ip-offload-status-indications).

Administrative applications (or overlying drivers) can determine the current task offload configuration of a network interface card (NIC) by querying the [OID\_TCP\_OFFLOAD\_CURRENT\_CONFIG](https://docs.microsoft.com/windows-hardware/drivers/network/oid-tcp-offload-current-config) OID.

The [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure that is associated with [OID\_TCP\_OFFLOAD\_CURRENT\_CONFIG](https://docs.microsoft.com/windows-hardware/drivers/network/oid-tcp-offload-current-config) specifies the following:

-   The header information, which includes the task offload version that the TCP/IP transport supports.

-   The checksum offload information, in an [**NDIS\_TCP\_IP\_CHECKSUM\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_ip_checksum_offload) structure.

-   The large send offload version 1 (LSOV1) information, in an [**NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V1**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_large_send_offload_v1) structure.

-   The Internet protocol security (IPsec) information, in an [**NDIS\_IPSEC\_OFFLOAD\_V1**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_ipsec_offload_v1) structure.

-   The large send offload version 2 (LSOV2) information, in an [**NDIS\_TCP\_LARGE\_SEND\_OFFLOAD\_V2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_large_send_offload_v2) structure.

-   The Internet protocol security (IPsecvOV) information in an [**NDIS\_IPSEC\_OFFLOAD\_V2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_ipsec_offload_v2) structure.

The following topics contain specific information for each type of offload service:

-   [Reporting a NIC's Checksum Capabilities](reporting-a-nic-s-checksum-capabilities.md)
-   [Reporting a NIC's LSOV1 TCP-Packet-Segmentation Capabilities](reporting-a-nic-s-lsov1-tcp-packet-segmentation-capabilities.md)
-   [Reporting a NIC's LSOV2 TCP-Packet-Segmentation Capabilities](reporting-a-nic-s-lsov2-tcp-packet-segmentation-capabilities.md)
-   [Reporting a NIC's IPsec Capabilities](reporting-a-nic-s-ipsec-capabilities.md)
    - \[The IPsec Task Offload feature is deprecated and should not be used.\]

 

 





