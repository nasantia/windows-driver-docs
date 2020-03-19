---
title: KSPROPERTY\_EXTDEVICE\_VERSION
description: The KSPROPERTY\_EXTDEVICE\_VERSION property retrieves the version of an external device.
ms.assetid: cb5133c9-b723-4d28-b591-8c65a8cc52a5
keywords: ["KSPROPERTY_EXTDEVICE_VERSION Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_EXTDEVICE_VERSION
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# KSPROPERTY\_EXTDEVICE\_VERSION


The KSPROPERTY\_EXTDEVICE\_VERSION property retrieves the version of an external device.

## <span id="ddk_ksproperty_extdevice_version_ks"></span><span id="DDK_KSPROPERTY_EXTDEVICE_VERSION_KS"></span>


### Usage Summary Table

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Get</th>
<th>Set</th>
<th>Target</th>
<th>Property descriptor type</th>
<th>Property value type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Device</p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_extdevice_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_EXTDEVICE_S&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_extdevice_s)"><strong>KSPROPERTY_EXTDEVICE_S</strong></a></p></td>
<td><p>WCHAR array</p></td>
</tr>
</tbody>
</table>

 

The property value (operation data) is WCHAR array that contains the external device's version. The array is a free-format string.

Remarks
-------

The **pawchString** member of the KSPROPERTY\_EXTDEVICE\_S structure describes the external device's version.

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
<td>Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## See also


[**KSPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

[**KSPROPERTY\_EXTDEVICE\_S**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_extdevice_s)

 

 






