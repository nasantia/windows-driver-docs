---
title: Obtaining the Current Settings of WOL Patterns
description: Obtaining the Current Settings of WOL Patterns
ms.assetid: 113ea75a-83d8-41aa-b61c-711ef90bccca
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Obtaining the Current Settings of WOL Patterns





Overlying drivers can use the [OID\_PM\_WOL\_PATTERN\_LIST](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pm-wol-pattern-list) OID query request to enumerate the wake-on-LAN (WOL) patterns that are set on an underlying network adapter. After a successful return from the query, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to a list of [**NDIS\_PM\_WOL\_PATTERN**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_pm_wol_pattern) structures that describe the currently added WOL patterns. For information about the contents of the **NDIS\_PM\_WOL\_PATTERN** structure, see [Adding and Deleting Wake on LAN Patterns](adding-and-deleting-wake-on-lan-patterns.md).

NDIS handles OID\_PM\_WOL\_PATTERN\_LIST OID requests on behalf of the miniport driver. Therefore, NDIS miniport drivers are not required to support OID\_PM\_WOL\_PATTERN\_LIST OID request.

 

 





