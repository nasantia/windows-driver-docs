---
title: OID_WWAN_UICC_FILE_STATUS
description: OID_WWAN_UICC_FILE_STATUS retrieves information about a specified UICC file.
ms.assetid: 1FD3E140-1CE3-416C-8CB4-27012363B60B
ms.date: 04/09/2019
keywords: 
 -OID_WWAN_UICC_FILE_STATUS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
ms.custom: 19H1
---

# OID_WWAN_UICC_FILE_STATUS

OID_WWAN_UICC_FILE_STATUS retrieves information about a specified UICC file. 

Query payloads contain an [**NDIS_WWAN_UICC_FILE_PATH**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_path) structure containing information about the target file. Miniport drivers must process Query requests asynchronously, initially returning NDIS_STATUS_INDICATION_REQUIRED to the original request before later sending an [NDIS_STATUS_WWAN_UICC_FILE_STATUS](ndis-status-wwan-uicc-file-status.md) status notification containing an [**NDIS_WWAN_UICC_FILE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_status) structure that describes the specified file. 

Set requests are not applicable.

## Remarks

For more information about usage of this OID, see [MB UICC application and file system access](mb-uicc-application-and-file-system-access.md).

## Requirements

|   |   |
| --- | --- |
| Version | Windows 10, version 1903 |
| Header | Ntddndis.h (include Ndis.h) |

## See also

[MB UICC application and file system access](mb-uicc-application-and-file-system-access.md)

[NDIS_STATUS_WWAN_UICC_UICC_FILE_STATUS](ndis-status-wwan-uicc-file-status.md)

[**NDIS_WWAN_UICC_FILE_PATH**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_path) 

[**NDIS_WWAN_UICC_FILE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_uicc_file_status)
