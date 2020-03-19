---
title: StorPortSpinLock rule (storport)
description: This rule verifies that locks that are acquired via StorPortAcquireSpinLock are promptly released via StorPortReleaseSpinLock.
ms.assetid: B7B918A0-3042-4961-8D33-EFDC15819D1F
ms.date: 05/21/2018
keywords: ["StorPortSpinLock rule (storport)"]
topic_type:
- apiref
api_name:
- StorPortSpinLock
api_type:
- NA
ms.localizationpriority: medium
---

# StorPortSpinLock rule (storport)


This rule verifies that locks that are acquired via **StorPortAcquireSpinLock** are promptly released via **StorPortReleaseSpinLock**. The miniport driver fails the rule if it attempts to acquire a lock that it had already acquired, or if it attempts to release a lock that it had not acquired. In addition, at the end of the dispatch or cancel routine, the driver should not hold any spin locks.

|              |          |
|--------------|----------|
| Driver model | Storport |

How to test
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">At compile time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Run <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a> and specify the <strong>StorPortSpinLock</strong> rule.</p>
Use the following steps to run an analysis of your code:
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">Prepare your code (use role type declarations).</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">Run Static Driver Verifier.</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">View and analyze the results.</a></li>
</ol>
<p>For more information, see <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">Using Static Driver Verifier to Find Defects in Drivers</a>.</p></td>
</tr>
</tbody>
</table>

Applies to
----------

[**StorPortAcquireSpinLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/storport/nf-storport-storportacquirespinlock)
[**StorPortReleaseSpinLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/storport/nf-storport-storportreleasespinlock)
 

 





