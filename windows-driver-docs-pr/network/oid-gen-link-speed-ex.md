---
title: OID_GEN_LINK_SPEED_EX
description: As a query, the OID_GEN_LINK_SPEED_EX OID provides the transmit and receive link speeds of an interface. Version Information Windows Vista and laterSupported. NDIS 6.0 and later miniport driversNot requested. For NDIS interface providers only.
ms.assetid: 86cc281b-3898-484c-9418-4408a45ebe71
ms.date: 08/08/2017
keywords: 
 -OID_GEN_LINK_SPEED_EX Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# OID\_GEN\_LINK\_SPEED\_EX


As a query, the OID\_GEN\_LINK\_SPEED\_EX OID provides the transmit and receive link speeds of an interface.

**Version Information**

<a href="" id="windows-vista-and-later"></a>Windows Vista and later  
Supported.

<a href="" id="ndis-6-0-and-later-miniport-drivers"></a>NDIS 6.0 and later miniport drivers  
Not requested. For NDIS interface providers only.

Remarks
-------

NDIS uses this OID to query the link speed of an [NDIS network interface](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-network-interfaces2) provider. Only NDIS interface providers, and therefore not miniport drivers or filter drivers, must support this OID as an OID request.

This OID returns the link speeds in an [**NDIS\_LINK\_SPEED**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_link_speed) structure.

Miniport drivers supply the link speed during initialization and provide updated link speeds with status indications.

To specify the link speeds in a miniport driver, set the **XmitLinkSpeed** and **RcvLinkSpeed** members of the [**NDIS\_MINIPORT\_ADAPTER\_GENERAL\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_miniport_adapter_general_attributes) structure that the miniport driver passes to the [**NdisMSetMiniportAttributes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsetminiportattributes) function.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Ntddndis.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


[**NDIS\_LINK\_SPEED**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_link_speed)

[**NDIS\_MINIPORT\_ADAPTER\_GENERAL\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_miniport_adapter_general_attributes)

[**NdisMSetMiniportAttributes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsetminiportattributes)

[NDIS Network Interface OIDs](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-network-interface-oids)

 

 




