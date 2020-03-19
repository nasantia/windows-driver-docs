---
title: FSCTL_QUERY_REFS_SMR_VOLUME_INFO control code
description: The FSCTL\_QUERY\_REFS\_SMR\_VOLUME\_INFO control code queries the Shingled Magnetic Recording (SMR) volume for its current state on space and garbage collection activities.
ms.assetid: 1318CF90-2449-407E-8C9E-825E571F4CDD
keywords: ["FSCTL_QUERY_REFS_SMR_VOLUME_INFO control code Installable File System Drivers"]
topic_type:
- apiref
api_name:
- FSCTL_QUERY_REFS_SMR_VOLUME_INFO
api_location:
- WinIoctl.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# FSCTL\_QUERY\_REFS\_SMR\_VOLUME\_INFO control code


The **FSCTL\_QUERY\_REFS\_SMR\_VOLUME\_INFO** control code queries the Shingled Magnetic Recording (SMR) volume for its current state on space and garbage collection activities.

To perform this operation, call the [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) function with the following parameters.

```ManagedCPlusPlus
BOOL 
DeviceIoControl( (HANDLE)       hDevice,         // handle to device
                    (DWORD)        FSCTL_QUERY_REFS_SMR_VOLUME_INFO, // dwIoControlCode
                    (LPDWORD)      lpInBuffer,      // input buffer
                    (DWORD)        nInBufferSize,   // size of input buffer
                    (LPDWORD)      lpOutBuffer,     // output buffer
                    (DWORD)        nOutBufferSize,  // size of output buffer
                    (LPDWORD)      lpBytesReturned, // number of bytes returned
                    (LPOVERLAPPED) lpOverlapped );  // OVERLAPPED structure
```

Parameters
----------

*hDevice* \[in\]  
A handle to the device. To obtain a device handle, call the [**CreateFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-createfilea) function.

*dwIoControlCode* \[in\]  
The control code for the operation. Use **FSCTL\_QUERY\_REFS\_SMR\_VOLUME\_INFO** for this operation.

*lpInBuffer*   
Not used with this operation; set to **NULL**.

*nInBufferSize* \[in\]  
Not used with this operation; set to zero.

*lpOutBuffer* \[out\]  
A pointer to a buffer that receives a [**REFS\_SMR\_VOLUME\_INFO\_OUTPUT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_refs_smr_volume_info_output) structure which specifies a volume's current state on space and garbage collection activities.

*nOutBufferSize* \[in\]  
The size of the output buffer, in bytes.

*lpBytesReturned* \[out\]  
A pointer to a variable that receives the size of the data stored in the output buffer, in bytes.

If the output buffer is too small, the call fails, [**GetLastError**](https://docs.microsoft.com/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns **ERROR\_INSUFFICIENT\_BUFFER**, and *lpBytesReturned* is zero.

If *lpOverlapped* is **NULL**, *lpBytesReturned* cannot be **NULL**. Even when an operation returns no output data and *lpOutBuffer* is **NULL**, [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) makes use of *lpBytesReturned*. After such an operation, the value of *lpBytesReturned* is meaningless.

If *lpOverlapped* is not **NULL**, *lpBytesReturned* can be **NULL**. If this parameter is not **NULL** and the operation returns data, *lpBytesReturned* is meaningless until the overlapped operation has completed. To retrieve the number of bytes returned, call [**GetOverlappedResult**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult). If the *hDevice* parameter is associated with an I/O completion port, you can retrieve the number of bytes returned by calling [**GetQueuedCompletionStatus**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-getqueuedcompletionstatus).

*lpOverlapped* \[in\]  
A pointer to an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure.

If *hDevice* was opened without specifying **FILE\_FLAG\_OVERLAPPED**, *lpOverlapped* is ignored.

If *hDevice* was opened with the **FILE\_FLAG\_OVERLAPPED** flag, the operation is performed as an overlapped (asynchronous) operation. In this case, *lpOverlapped* must point to a valid [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure that contains a handle to an event object. Otherwise, the function fails in unpredictable ways.

For overlapped operations, [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) returns immediately, and the event object is signaled when the operation has been completed. Otherwise, the function does not return until the operation has been completed or an error occurs.

Return value
------------

If the operation completes successfully, [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) returns a nonzero value.

If the operation fails or is pending, [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) returns zero. To get extended error information, call [**GetLastError**](https://docs.microsoft.com/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

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
<td align="left"><p>Available starting with Windows 10, version 1709.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">WinIoctl.h</td>
</tr>
</tbody>
</table>

## See also


[**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol)

[**REFS\_SMR\_VOLUME\_INFO\_OUTPUT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_refs_smr_volume_info_output)

[**REFS\_SMR\_VOLUME\_GC\_STATE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ne-ntifs-_refs_smr_volume_gc_state)

 

 






