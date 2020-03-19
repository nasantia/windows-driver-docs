---
title: Obtaining the Current Parameter Settings of Low Power Protocol Offloads
description: Obtaining the Current Parameter Settings of Low Power Protocol Offloads
ms.assetid: 53d8535f-0615-4ba2-92f4-1c20a7d12c8d
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Obtaining the Current Parameter Settings of Low Power Protocol Offloads





A protocol driver can use [OID\_PM\_PROTOCOL\_OFFLOAD\_LIST](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pm-protocol-offload-list) OID query to get a list of all the protocols that have been offloaded by that protocol on a network adapter. After a successful return from the query, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to a list of [**NDIS\_PM\_PROTOCOL\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_pm_protocol_offload) structures that describe the currently active protocol offloads. For information about the contents of the **NDIS\_PM\_PROTOCOL\_OFFLOAD** structure, see [Adding and Deleting Low Power Protocol Offloads](adding-and-deleting-low-power-protocol-offloads.md).

NDIS handles [OID\_PM\_PROTOCOL\_OFFLOAD\_LIST](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pm-protocol-offload-list) OID and GUID\_PM\_PROTOCOL\_OFFLOAD\_LIST WMI requests on behalf of the miniport driver. Therefore, NDIS miniport drivers are not required to support OID\_PM\_PROTOCOL\_OFFLOAD\_LIST OID request.

Overlying drivers can use the [OID\_PM\_GET\_PROTOCOL\_OFFLOAD](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pm-get-protocol-offload) method OID to get parameter settings for a low power protocol offload from a miniport driver. The **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure initially contains a pointer to a protocol offload identifier. After a successful return from the method request, the **InformationBuffer** member of the **NDIS\_OID\_REQUEST** structure contains a pointer to an [**NDIS\_PM\_PROTOCOL\_OFFLOAD**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_pm_protocol_offload) structure.

 

 





