---
title: NDIS_STATUS_WWAN_DEVICE_SERVICE_SESSION
description: Miniport drivers use the NDIS_STATUS_WWAN_DEVICE_SERVICE_SESSION indication to report the completion of a device service session state change originated by OID_WWAN_DEVICE_SERVICE_SESSION.NDIS_WWAN_DEVICE_SERVICE_SESSION_INFO structure.
ms.assetid: 0A3D8323-20F1-4405-97D4-0E497946118E
ms.date: 07/18/2017
keywords:
 - NDIS_STATUS_WWAN_DEVICE_SERVICE_SESSION Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# NDIS\_STATUS\_WWAN\_DEVICE\_SERVICE\_SESSION


Miniport drivers use the NDIS\_STATUS\_WWAN\_DEVICE\_SERVICE\_SESSION indication to report the completion of a device service session state change originated by [OID\_WWAN\_DEVICE\_SERVICE\_SESSION](https://docs.microsoft.com/windows-hardware/drivers/network/oid-wwan-device-service-session).

Miniport drivers cannot use this notification to send unsolicited events.

This notification uses the [**NDIS\_WWAN\_DEVICE\_SERVICE\_SESSION\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_device_service_session_info) structure.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Supported starting with Windows 8.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ndis.h</td>
</tr>
</tbody>
</table>

## See also


[OID\_WWAN\_DEVICE\_SERVICE\_SESSION](https://docs.microsoft.com/windows-hardware/drivers/network/oid-wwan-device-service-session)

[**NDIS\_WWAN\_DEVICE\_SERVICE\_SESSION\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_device_service_session_info)

 

 




