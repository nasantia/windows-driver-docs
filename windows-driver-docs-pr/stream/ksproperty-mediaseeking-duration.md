---
title: KSPROPERTY\_MEDIASEEKING\_DURATION
description: The KSPROPERTY\_MEDIASEEKING\_DURATION property retrieves the media duration on a filter.
ms.assetid: f84ff468-7cf6-4948-afee-a28ee365760d
keywords: ["KSPROPERTY_MEDIASEEKING_DURATION Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_MEDIASEEKING_DURATION
api_location:
- ks.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# KSPROPERTY\_MEDIASEEKING\_DURATION


The KSPROPERTY\_MEDIASEEKING\_DURATION property retrieves the media duration on a filter.

## <span id="ddk_ksproperty_mediaseeking_duration_ks"></span><span id="DDK_KSPROPERTY_MEDIASEEKING_DURATION_KS"></span>


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
<th>Property Descriptor Type</th>
<th>Property Value Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Filter</p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p>LONGLONG</p></td>
</tr>
</tbody>
</table>

 

Remarks
-------

This property returns the media duration as a value of type LONGLONG.

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
<td>Ks.h (include Ks.h)</td>
</tr>
</tbody>
</table>

## See also


[KSPROPSETID\_MediaSeeking](kspropsetid-mediaseeking.md)

 

 






