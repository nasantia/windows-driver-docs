---
title: FILE_LOCK structure
description: The operating system uses the opaque FILE\_LOCK structure to support the locking of files.
ms.assetid: 89df2075-c542-4105-847f-9bc7ae4dab50
keywords: ["FILE_LOCK structure Installable File System Drivers", "PFILE_LOCK structure pointer Installable File System Drivers"]
topic_type:
- apiref
api_name:
- FILE_LOCK
api_location:
- ntifs.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# FILE\_LOCK structure


The operating system uses the opaque FILE\_LOCK structure to support the locking of files.

Syntax
------

```ManagedCPlusPlus
typedef struct _FILE_LOCK {
  PCOMPLETE_LOCK_IRP_ROUTINE CompleteLockIrpRoutine;
  PUNLOCK_ROUTINE            UnlockRoutine;
  BOOLEAN                    FastIoIsQuestionable;
  BOOLEAN                    SpareC[3];
  PVOID                      LockInformation;
  FILE_LOCK_INFO             LastReturnedLockInfo;
  PVOID                      LastReturnedLock;
  volatile LONG              LockRequestsInProgress;
} FILE_LOCK, *PFILE_LOCK;
```

Members
-------

**CompleteLockIrpRoutine**  
Reserved for system use.

**UnlockRoutine**  
Reserved for system use.

**FastIoIsQuestionable**  
Reserved for system use.

**SpareC**  
Reserved for system use.

**LockInformation**  
Reserved for system use.

**LastReturnedLockInfo**  
Reserved for system use.

**LastReturnedLock**  
Reserved for system use.

**LockRequestsInProgress**  
Reserved for system use.

Remarks
-------

File system drivers, legacy filesystem filter drivers and minifilters can use a variety of routines to create and use FILE\_LOCK objects, as well as to test for read/write access to files.

-   To allocate a FILE\_LOCK object, call [**FsRtlAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock) or [**FltAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocatefilelock).

-   To initialize an uninitialized FILE\_LOCK object, call [**FsRtlInitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlinitializefilelock) or [**FltInitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltinitializefilelock). Be aware that a FILE\_LOCK returned from [**FsRtlAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock) or [**FltAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocatefilelock) is already initialized.

-   To uninitialize a FILE\_LOCK object, call [**FsRtlUninitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtluninitializefilelock) or [**FltUninitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltuninitializefilelock).

-   To free a FILE\_LOCK object that is allocated by the [**FsRtlAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock) routine, call [**FsRtlFreeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlfreefilelock). To free a FILE\_LOCK object that is allocated by the [**FltAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocatefilelock) routine, call [**FltFreeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfreefilelock).

After a FILE\_LOCK has been initialized, routines such as [**FsRtlCheckLockForReadAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlchecklockforreadaccess), [**FltCheckLockForWriteAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltchecklockforwriteaccess), and [**FsRtlFastCheckLockForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlfastchecklockforread) can be used to determine if the file can be accessed by other threads.

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
<td align="left"><p>Available in Microsoft Windows 2000, and later versions of the Windows operating system.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Ntifs.h (include FltKernel.h or Ntifs.h)</td>
</tr>
</tbody>
</table>

## See also


[**FltAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocatefilelock)

[**FltCheckLockForReadAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltchecklockforreadaccess)

[**FltCheckLockForWriteAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltchecklockforwriteaccess)

[**FltInitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltinitializefilelock)

**FltInitializeFileLock**
[**FsRtlAllocateFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock)

[**FsRtlCheckLockForReadAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlchecklockforreadaccess)

[**FsRtlCheckLockForWriteAccess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlchecklockforwriteaccess)

[**FsRtlFastCheckLockForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlfastchecklockforread)

[**FsRtlFastCheckLockForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlfastchecklockforwrite)

[**FsRtlInitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlinitializefilelock)

[**FsRtlUninitializeFileLock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtluninitializefilelock)

 

 






