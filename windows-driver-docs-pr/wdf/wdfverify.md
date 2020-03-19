---
title: WDFVERIFY macro
description: The WDFVERIFY macro tests a logical expression and, if the expression evaluates to FALSE, breaks into the kernel debugger.
ms.assetid: 9dc19299-7eda-42fb-811e-ba8dc5c1cdb5
keywords:
 - WDFVERIFY macro
ms.date: 08/23/2017
ms.localizationpriority: medium
---

# WDFVERIFY macro


\[Applies to KMDF only\]

The **WDFVERIFY** macro tests a logical expression and, if the expression evaluates to **FALSE**, breaks into the kernel debugger.

Syntax
------

```ManagedCPlusPlus
VOID WDFVERIFY(
    exp
);
```

Parameters
----------

*exp*   
A logical expression that WDFVERIFY tests.

Return value
------------

None

Remarks
-------

The code for the **WDFVERIFY** macro is included in your driver's binary when you build your driver in a release configuration or a debug configuration.

The **WDFVERIFY** code breaks into a kernel debugger only if the **VerifyOn** value is set in the registry. For more information about registry entries that you can use to debug your driver, see [Registry Entries for Debugging Framework-Based Drivers](https://docs.microsoft.com/windows-hardware/drivers/wdf/registry-values-for-debugging-kmdf-drivers).

For more information about debugging your driver, see [Debugging a KMDF Driver](https://docs.microsoft.com/windows-hardware/drivers/wdf/debugging-a-wdf-driver).

Examples
--------

The following code example breaks into the debugger if an attempt to reuse a request object fails.

```cpp
status = WdfRequestReuse(Request, &params);
WDFVERIFY(NT_SUCCESS(status));
```

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Target platform</p></td>
<td><a href="https://go.microsoft.com/fwlink/p/?linkid=531356" data-raw-source="[Universal](https://go.microsoft.com/fwlink/p/?linkid=531356)">Universal</a></td>
</tr>
<tr class="even">
<td><p>Minimum KMDF version</p></td>
<td><p>1.0</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wdfassert.h (include Wdf.h)</td>
</tr>
</tbody>
</table>

## See also


[**VERIFY_IS_IRQL_PASSIVE_LEVEL**](verify-is-irql-passive-level.md)

 

 






