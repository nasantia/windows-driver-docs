---
title: WlanTimedConnectionRoaming rule (ndis)
description: The WlanTimedConnectionRoaming rule specifies that the NDIS miniport driver finishes the wireless LAN (WLAN) connection/roaming operations within 10 seconds.
ms.assetid: 0961C34B-FAD8-49ED-A0FD-5D790E973C4D
ms.date: 05/21/2018
keywords: ["WlanTimedConnectionRoaming rule (ndis)"]
topic_type:
- apiref
api_name:
- WlanTimedConnectionRoaming
api_type:
- NA
ms.localizationpriority: medium
---

# WlanTimedConnectionRoaming rule (ndis)


The **WlanTimedConnectionRoaming** rule specifies that the NDIS miniport driver finishes the wireless LAN (WLAN) connection/roaming operations within 10 seconds.

|              |      |
|--------------|------|
| Driver model | NDIS |

|                                   |                                                                                                                                        |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Bug check(s) found with this rule | [**Bug Check 0xC4: DRIVER\_VERIFIER\_DETECTED\_VIOLATION**](https://docs.microsoft.com/windows-hardware/drivers/debugger/bug-check-0xc4--driver-verifier-detected-violation) ( 0x00094008) |

How to test
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">At run time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Run <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier)">Driver Verifier</a> and select the <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/ndis-wifi-verification" data-raw-source="[NDIS/WIFI verification](https://docs.microsoft.com/windows-hardware/drivers/devtest/ndis-wifi-verification)">NDIS/WIFI verification</a> option.</p></td>
</tr>
</tbody>
</table>

 

Applies to
----------

[**MiniportHaltEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_halt)
[**MiniportOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_oid_request)
[**NdisMIndicateStatusEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismindicatestatusex)
See also
--------

[General Connection Operation Guidelines](https://docs.microsoft.com/windows-hardware/drivers/network/general-connection-operation-guidelines)
 

 





