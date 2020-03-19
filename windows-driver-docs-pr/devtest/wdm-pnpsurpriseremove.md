---
title: PnpSurpriseRemove rule (wdm)
description: The PnpSurpriseRemove rule specifies that the driver does not call IoDeleteDevice or IoDetachDevice while processing an IRP\_MN\_SURPRISE\_REMOVAL request.
ms.assetid: 58553c78-04c3-423c-bf68-69d5a8fbfa9b
ms.date: 05/21/2018
keywords: ["PnpSurpriseRemove rule (wdm)"]
topic_type:
- apiref
api_name:
- PnpSurpriseRemove
api_type:
- NA
ms.localizationpriority: medium
---

# PnpSurpriseRemove rule (wdm)


The **PnpSurpriseRemove** rule specifies that the driver does not call IoDeleteDevice or IoDetachDevice while processing an [**IRP\_MN\_SURPRISE\_REMOVAL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal) request.

The PnP manager sends the [**IRP\_MN\_SURPRISE\_REMOVAL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal) request to notify drivers that a device is no longer available for I/O operations and that it has probably been unexpectedly removed from the computer.

-   All PnP drivers must handle [**IRP\_MN\_SURPRISE\_REMOVAL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal) request.
-   The driver must not call [**IoDeleteDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodeletedevice) or [**IoDetachDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodetachdevice) on device objects until the IRP\_MN\_SURPRISE\_REMOVAL IRP succeeds and all open handles to the device are closed.
-   The PnP manager then sends an [**IRP\_MN\_REMOVE\_DEVICE**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-remove-device) request to the device stack. In response to the remove IRP, drivers detach their device objects from the stack and delete them.

For more information about how a driver should respond to [**IRP\_MN\_SURPRISE\_REMOVAL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal) request, see [**Handling an IRP\_MN\_SURPRISE\_REMOVAL Request**](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-an-irp-mn-surprise-removal-request)

|              |     |
|--------------|-----|
| Driver model | WDM |

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
<td align="left"><p>Run <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a> and specify the <strong>PnpSurpriseRemove</strong> rule.</p>
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

[**IoDeleteDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodeletedevice)
[**IoDetachDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iodetachdevice)
See also
--------

[**Handling an IRP\_MN\_SURPRISE\_REMOVAL Request**](https://docs.microsoft.com/windows-hardware/drivers/kernel/handling-an-irp-mn-surprise-removal-request)
[Analyzing a Driver Using Verification and Code Analysis Tools](https://docs.microsoft.com/windows-hardware/drivers)
[**IRP\_MN\_SURPRISE\_REMOVAL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-surprise-removal)
[**IRP\_MN\_REMOVE\_DEVICE**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-remove-device)
 

 





