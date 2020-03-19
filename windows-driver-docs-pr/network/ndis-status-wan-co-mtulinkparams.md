---
title: NDIS_STATUS_WAN_CO_MTULINKPARAMS
description: The NDIS_STATUS_WAN_CO_MTULINKPARAMS status indicates that the link speed and send window parameters have changed for a particular VC that is active on a CoNDIS miniport adapter.
ms.assetid: 1ba67087-08aa-4359-9884-e47bf634fda5
ms.date: 07/18/2017
keywords:
 - NDIS_STATUS_WAN_CO_MTULINKPARAMS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# NDIS\_STATUS\_WAN\_CO\_MTULINKPARAMS


The NDIS\_STATUS\_WAN\_CO\_MTULINKPARAMS status indicates that the link speed and send window parameters have changed for a particular VC that is active on a CoNDIS miniport adapter.

Remarks
-------

The **StatusBuffer** member of the [**NDIS\_STATUS\_INDICATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication) structure contains a pointer to a [**WAN\_CO\_MTULINKPARAMS**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff565821(v=vs.85)) structure. The WAN\_CO\_MTULINKPARAMS structure describes new parameters for the VC.

For more information about NDIS\_STATUS\_WAN\_CO\_MTULINKPARAMS, see [Indicating CoNDIS WAN Miniport Driver Status](https://docs.microsoft.com/windows-hardware/drivers/network/indicating-condis-wan-miniport-driver-status). For more information about the CoNDIS WAN interface, see [Implementing CoNDIS WAN Miniport Drivers](https://docs.microsoft.com/windows-hardware/drivers/network/implementing-condis-wan-miniport-drivers).

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
<td><p>Supported in NDIS 6.20 and later.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ndis.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


[**NDIS\_STATUS\_INDICATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication)

[**WAN\_CO\_MTULINKPARAMS**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff565821(v=vs.85))

 

 




