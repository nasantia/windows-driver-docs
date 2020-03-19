---
title: FltReleaseResource routine
description: The FltReleaseResource routine releases a specified resource owned by the current thread.
ms.assetid: 2884c596-77ec-4cba-b6cb-000d96cc6342
keywords: ["FltReleaseResource routine Installable File System Drivers"]
topic_type:
- apiref
api_name:
- FltReleaseResource
api_location:
- fltmgr.sys
api_type:
- DllExport
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# FltReleaseResource routine


The **FltReleaseResource** routine releases a specified resource owned by the current thread.

Syntax
------

```ManagedCPlusPlus
VOID FltReleaseResource(
  _Inout_ PERESOURCE Resource
);
```

Parameters
----------

*Resource* \[in, out\]  
Pointer to the opaque ERESOURCE structure for the resource to be released.

Return value
------------

None

Remarks
-------

**FltReleaseResource** releases a resource that was previously acquired by calling [**FltAcquireResourceExclusive**](fltacquireresourceexclusive.md) or [**FltAcquireResourceShared**](fltacquireresourceshared.md).

**FltReleaseResource** is a wrapper for [**ExReleaseResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exreleaseresourcelite) that reenables normal kernel APC delivery.

Because **FltReleaseResource** reenables normal kernel APC delivery, it is not necessary to call [**KeLeaveCriticalRegion**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keleavecriticalregion) or [**FsRtlExitFileSystem**](fsrtlexitfilesystem.md) after calling **FltReleaseResource**.

To acquire a resource for exclusive access, call [**FltAcquireResourceExclusive**](fltacquireresourceexclusive.md).

To acquire a resource for shared access, call [**FltAcquireResourceShared**](fltacquireresourceshared.md).

To delete a resource from the system's resource list, call [**ExDeleteResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exdeleteresourcelite).

To initialize a resource for reuse, call [**ExReinitializeResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exreinitializeresourcelite).

For more information about ERESOURCE structures, see [Introduction to ERESOURCE Routines](https://docs.microsoft.com/windows-hardware/drivers/kernel/introduction-to-eresource-routines) in the Kernel Architecture Design Guide.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Target platform</p></td>
<td align="left"><a href="https://go.microsoft.com/fwlink/p/?linkid=531356" data-raw-source="[Universal](https://go.microsoft.com/fwlink/p/?linkid=531356)">Universal</a></td>
</tr>
<tr class="even">
<td align="left"><p>Version</p></td>
<td align="left"><p>This routine is available on Microsoft Windows XP SP2, Microsoft Windows Server 2003 SP1, and later.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">Fltkernel.h (include Fltkernel.h)</td>
</tr>
<tr class="even">
<td align="left"><p>Library</p></td>
<td align="left">FltMgr.lib</td>
</tr>
<tr class="odd">
<td align="left"><p>DLL</p></td>
<td align="left">Fltmgr.sys</td>
</tr>
<tr class="even">
<td align="left"><p>IRQL</p></td>
<td align="left"><p>&lt;= DISPATCH_LEVEL</p></td>
</tr>
</tbody>
</table>

## See also


[**ExDeleteResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exdeleteresourcelite)

[**ExInitializeResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exinitializeresourcelite)

[**ExReinitializeResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exreinitializeresourcelite)

[**ExReleaseResourceLite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exreleaseresourcelite)

[**FltAcquireResourceExclusive**](fltacquireresourceexclusive.md)

[**FltAcquireResourceShared**](fltacquireresourceshared.md)

[**FsRtlExitFileSystem**](fsrtlexitfilesystem.md)

[**KeLeaveCriticalRegion**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keleavecriticalregion)

 

 






