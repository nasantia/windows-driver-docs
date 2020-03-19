---
title: Determining the RSC Capabilities of a Network Adapter
description: A receive segment coalescing (RSC)-capable miniport driver reports its RSC capability by means of the NDIS_OFFLOAD structure that it passes to NdisMSetMiniportAttributes.
ms.assetid: 043A09F9-7D5D-4401-9645-19FDBD614659
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Determining the RSC Capabilities of a Network Adapter


A receive segment coalescing (RSC)-capable miniport driver reports its RSC capability by means of the [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure that it passes to [**NdisMSetMiniportAttributes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsetminiportattributes).

## Reporting RSC Capability


In the [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure, the **Header** member must be set as follows:

-   The **Revision** member must be set to **NDIS\_OFFLOAD\_REVISION\_3**.
-   The **Size** member must be set to **NDIS\_SIZEOF\_NDIS\_OFFLOAD\_REVISION\_3**.

To report its support for RSC, a miniport driver can set the following members in the [**NDIS\_TCP\_RECV\_SEG\_COALESCE\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_tcp_recv_seg_coalesce_offload) structure, which is stored in the **Rsc** member of the [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure:

-   Set the **IPv4.Enabled** member to **TRUE** to indicate support for RSC for IPv4.

-   Set the **IPv6.Enabled** member to **TRUE** to indicate support for RSC for IPv6.

The miniport driver must support RSC for at least IEEE 802.3 encapsulation. In addition, it can support RSC for any other encapsulations. If it does not support RSC for some encapsulation, and it receives packets of that encapsulation, the driver must indicate the packets up the stack normally.

## Querying RSC Capability


To determine whether a miniport driver supports RSC, protocol drivers and other drivers can issue the [OID\_TCP\_OFFLOAD\_HARDWARE\_CAPABILITIES](https://docs.microsoft.com/windows-hardware/drivers/network/oid-tcp-offload-hardware-capabilities) OID request, which will return an [**NDIS\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_offload) structure.

 

 





