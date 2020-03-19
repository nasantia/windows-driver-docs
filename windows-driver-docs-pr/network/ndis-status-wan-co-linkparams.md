---
title: NDIS_STATUS_WAN_CO_LINKPARAMS
description: The NDIS_STATUS_WAN_CO_FRAGMENT status indicates that parameters for a particular VC that is active on a CoNDIS miniport adapter have changed.
ms.assetid: a28460fc-c9e6-49c4-949a-badd3491cdd6
ms.date: 07/18/2017
keywords:
 - NDIS_STATUS_WAN_CO_LINKPARAMS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# NDIS\_STATUS\_WAN\_CO\_LINKPARAMS


The NDIS\_STATUS\_WAN\_CO\_FRAGMENT status indicates that parameters for a particular VC that is active on a CoNDIS miniport adapter have changed.

Remarks
-------

The **StatusBuffer** member of the [**NDIS\_STATUS\_INDICATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication) structure contains a pointer to a [**WAN\_CO\_LINKPARAMS**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff565819(v=vs.85)) structure. The WAN\_CO\_LINKPARAMS structure describes new parameters for the VC.

For more information about NDIS\_STATUS\_WAN\_CO\_LINKPARAMS, see [Indicating CoNDIS WAN Miniport Driver Status](https://docs.microsoft.com/windows-hardware/drivers/network/indicating-condis-wan-miniport-driver-status). For more information about the CoNDIS WAN interface, see [Implementing CoNDIS WAN Miniport Drivers](https://docs.microsoft.com/windows-hardware/drivers/network/implementing-condis-wan-miniport-drivers).

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
<td><p>Supported for NDIS 6.0 and NDIS 5.1 drivers in Windows Vista. Supported for NDIS 5.1 drivers in Windows XP.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ndis.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


[**NDIS\_STATUS\_INDICATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication)

[**WAN\_CO\_LINKPARAMS**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff565819(v=vs.85))

 

 




