---
title: NDIS_STATUS_WWAN_UICC_FILE_STATUS
description: Miniport drivers use the NDIS_STATUS_WWAN_UICC_FILE_STATUS notification to inform the mobile broadband (MB) service about the completion of a previous OID_WWAN_UICC_FILE_STATUS Query request.
ms.assetid: ABC19EDC-E414-4783-BC3B-ECABDF06C0C5
ms.date: 04/09/2019
keywords: 
 -NDIS_STATUS_WWAN_UICC_FILE_STATUS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
ms.custom: 19H1
---

# NDIS_STATUS_WWAN_UICC_FILE_STATUS

Miniport drivers use the **NDIS_STATUS_WWAN_UICC_FILE_STATUS** notification to inform the mobile broadband (MB) service about the completion of a previous [OID_WWAN_UICC_FILE_STATUS](oid-wwan-uicc-file-status.md) Query request.

Unsolicited events are not applicable.

This notification uses the [**NDIS_WWAN_UICC_FILE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_status) structure.

## Requirements

|   |   |
| --- | --- |
| Version | Windows 10, version 1903 |
| Header | Ntddndis.h (include Ndis.h) |

## See also

[MB UICC application and file system access](mb-uicc-application-and-file-system-access.md)

[OID_WWAN_UICC_FILE_STATUS](oid-wwan-uicc-file-status.md)

[**NDIS_WWAN_UICC_FILE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_status)
