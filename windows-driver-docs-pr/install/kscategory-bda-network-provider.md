---
title: KSCATEGORY_BDA_NETWORK_PROVIDER
description: KSCATEGORY_BDA_NETWORK_PROVIDER
ms.assetid: a73f7ea3-19bf-4328-a96f-f28ee91db242
keywords: ["KSCATEGORY_BDA_NETWORK_PROVIDER Device and Driver Installation"]
topic_type:
- apiref
api_name:
- KSCATEGORY_BDA_NETWORK_PROVIDER
api_location:
- Bdamedia.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
---

# KSCATEGORY_BDA_NETWORK_PROVIDER


The KSCATEGORY_BDA_NETWORK_PROVIDER [device interface class](https://docs.microsoft.com/windows-hardware/drivers/install/device-interface-classes) is defined for the [kernel streaming](https://docs.microsoft.com/windows-hardware/drivers/stream/streaming-minidrivers2) (KS) functional category for a network provider in the [broadcast driver architecture](https://docs.microsoft.com/windows-hardware/drivers/ddi/_stream/index) (BDA).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attribute</th>
<th align="left">Setting</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Identifier</p></td>
<td align="left"><p>KSCATEGORY_BDA_NETWORK_PROVIDER</p></td>
</tr>
<tr class="even">
<td align="left"><p>Class GUID</p></td>
<td align="left"><p>{71985F4B-1CA1-11d3-9CC8-00C04F7971E0}</p></td>
</tr>
</tbody>
</table>

 

Remarks
-------

Drivers for BDA devices register instances of KSCATEGORY_BDA_NETWORK_PROVIDER to indicate to the operating system that the devices support a BDA network provider filter.

For more information, see [BDA Filter Category GUIDs](https://docs.microsoft.com/windows-hardware/drivers/stream/bda-filter-category-guids).

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>Available in Windows XP and later versions of Windows. Available in Windows 2000 with DirectX 9.0A installed.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Bdamedia.h (include Bdamedia.h)</td>
</tr>
</tbody>
</table>

 

 





