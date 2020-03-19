---
title: KsCallbackReturn rule ()
description: The KsCallbackReturn rule specifies that a kernel-streaming (KS) miniport driver callback function returns only allowed status values.
ms.assetid: 1779301C-5C2C-471F-88D8-3E5F2C90357D
ms.date: 05/21/2018
keywords: ["KsCallbackReturn rule ()"]
topic_type:
- apiref
api_name:
- KsCallbackReturn
api_type:
- NA
ms.localizationpriority: medium
---

# KsCallbackReturn rule ()


The KsCallbackReturn rule specifies that a kernel-streaming (KS) miniport driver callback function returns only allowed status values.

|              |     |
|--------------|-----|
| Driver model | KS  |

|                                   |                                                                                                                                       |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Bug check(s) found with this rule | [**Bug Check 0xC4: DRIVER\_VERIFIER\_DETECTED\_VIOLATION**](https://docs.microsoft.com/windows-hardware/drivers/debugger/bug-check-0xc4--driver-verifier-detected-violation) (0x00081005) |

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
<td align="left"><p>To verify this rule, open a Command Prompt window. Enter a Driver Verifier command and specify <strong>/domain ks</strong>.</p>
<p>For example:</p>
<p><strong>verifier /domain ks</strong> [<em>options</em>] <strong>/driver</strong> <em>&lt;yourdriver&gt;</em></p>
<p>For more information, see <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier)">Driver Verifier</a>.</p></td>
</tr>
</tbody>
</table>

 

See also
--------

[Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier)
[*AVStrMiniPinSetDeviceState*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nc-ks-pfnkspinsetdevicestate)
[*AVStrMiniPinSetDataFormat*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nc-ks-pfnkspinsetdataformat)
 

 





