---
title: NDIS_STATUS_WWAN_SYS_CAPS_INFO
description: Miniport drivers use the NDIS_STATUS_WWAN_SYS_CAPS_INFO notification to inform the MB service about the completion of a previous OID_WWAN_SYS_CAPS_INFO query request.
ms.assetid: 653A35EC-29BB-458D-B33C-41EF6EF47A6E
ms.date: 07/18/2017
keywords:
 - NDIS_STATUS_WWAN_SYS_CAPS_INFO Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# NDIS\_STATUS\_WWAN\_SYS\_CAPS\_INFO


Miniport drivers use the **NDIS\_STATUS\_WWAN\_SYS\_CAPS\_INFO** notification to inform the MB service about the completion of a previous [OID\_WWAN\_SYS\_CAPS\_INFO](https://docs.microsoft.com/windows-hardware/drivers/network/oid-wwan-sys-caps) query request.

Miniport drivers cannot use this notification to send unsolicited events.

This notification uses the [**NDIS\_WWAN\_SYS\_CAPS\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_sys_caps_info) structure.

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
<td><p>Windows 10, version 1703</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ndis.h</td>
</tr>
</tbody>
</table>

## See also


[OID\_WWAN\_SYS\_CAPS\_INFO](https://docs.microsoft.com/windows-hardware/drivers/network/oid-wwan-sys-caps)

[**NDIS\_WWAN\_SYS\_CAPS\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_sys_caps_info)

 

 




