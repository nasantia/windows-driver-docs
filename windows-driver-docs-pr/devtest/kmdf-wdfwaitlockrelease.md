---
title: WdfWaitlockRelease rule (kmdf)
description: The WdfWaitlockRelease rule specifies that calls to WdfWaitLockAcquire and WdfWaitLockRelease are used in a balanced way within a KMDF event callback function.
ms.assetid: 4ac60469-b9a3-4777-865b-f03d5a4da8ed
ms.date: 05/21/2018
keywords: ["WdfWaitlockRelease rule (kmdf)"]
topic_type:
- apiref
api_name:
- WdfWaitlockRelease
api_type:
- NA
ms.localizationpriority: medium
---

# WdfWaitlockRelease rule (kmdf)


The **WdfWaitlockRelease** rule specifies that calls to [**WdfWaitLockAcquire**](https://msdn.microsoft.com/library/windows/hardware/ff551168) and [**WdfWaitLockRelease**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfsync/nf-wdfsync-wdfwaitlockrelease) are used in a balanced way within a KMDF event callback function. When the KMDF event callback function returns, the driver should not hold the framework spin lock object that was obtained by a previous call to **WdfWaitLockAcquire**.

|              |      |
|--------------|------|
| Driver model | KMDF |

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
<td align="left"><p>Run <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a> and specify the <strong>WdfWaitlockRelease</strong> rule.</p>
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

[**WdfWaitLockAcquire**](https://msdn.microsoft.com/library/windows/hardware/ff551168)
[**WdfWaitLockRelease**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfsync/nf-wdfsync-wdfwaitlockrelease)
 

 





