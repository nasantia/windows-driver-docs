---
title: FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL union
description: Union component used when the MajorFunction field of the FLT_IO_PARAMETER_BLOCK structure for the operation is IRP_MJ_FILE_SYSTEM_CONTROL.
ms.assetid: d90b9f23-9fae-46e8-b68c-1ba11b3fa17a
keywords: ["FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL union Installable File System Drivers", "FLT_PARAMETERS union Installable File System Drivers", "PFLT_PARAMETERS union pointer Installable File System Drivers"]
topic_type:
- apiref
api_name:
- FLT_PARAMETERS
api_location:
- fltkernel.h
api_type:
- HeaderDef
ms.date: 02/04/2020
ms.localizationpriority: medium
---

# FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL union

Union component used when the **MajorFunction** field of the [**FLT_IO_PARAMETER_BLOCK**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block) structure for the operation is [**IRP_MJ_FILE_SYSTEM_CONTROL**](irp-mj-file-system-control.md).

## Syntax

```ManagedCPlusPlus
typedef union _FLT_PARAMETERS {
  ...   ;
  union {
    struct {
      PVPB           Vpb;
      PDEVICE_OBJECT DeviceObject;
    } VerifyVolume;
    struct {
      ULONG                   OutputBufferLength;
      ULONG POINTER_ALIGNMENT InputBufferLength;
      ULONG POINTER_ALIGNMENT FsControlCode;
    } Common;
    struct {
      ULONG                    OutputBufferLength;
      ULONG POINTER_ALIGNMENT  InputBufferLength;
      ULONG POINTER_ALIGNMENT  FsControlCode;
      PVOID                    InputBuffer;
      PVOID                    OutputBuffer;
      PMDL                     OutputMdlAddress;
    } Neither;
    struct {
      ULONG                   OutputBufferLength;
      ULONG POINTER_ALIGNMENT InputBufferLength;
      ULONG POINTER_ALIGNMENT FsControlCode;
      PVOID                   SystemBuffer;
    } Buffered;
    struct {
      ULONG                   OutputBufferLength;
      ULONG POINTER_ALIGNMENT InputBufferLength;
      ULONG POINTER_ALIGNMENT FsControlCode;
      PVOID                   InputSystemBuffer;
      PVOID                   OutputBuffer;
      PMDL                    OutputMdlAddress;
    } Direct;
  } FileSystemControl;
  ...   ;
} FLT_PARAMETERS, *PFLT_PARAMETERS;
```

## Members

**FileSystemControl**  
Structure containing the following members.

**VerifyVolume**  
Union component used for IRP_MN_VERIFY_VOLUME operations.

**Vpb**  
Pointer to the volume parameter block (VPB) for the volume to be verified.

**DeviceObject**  
Pointer to the device object for the volume to be verified.

**Common**  
Union component used for all buffering methods for IRP_MN_KERNEL_CALL and IRP_MN_USER_FS_REQUEST operations.

**OutputBufferLength**  
Length, in bytes, of the buffer that the **Neither.OutputBuffer** or **Direct.OutputBuffer** member points to.

**InputBufferLength**  
Length, in bytes, of the buffer that the **Neither.InputBuffer**, **Buffered.SystemBuffer**, or **Direct.InputSystemBuffer** member points to.

**FsControlCode**  
FSCTL function code to be passed to the file system, file system filter, or minifilter driver for the target device.

For detailed information about IOCTL and FSCTL requests, see [Using I/O Control Codes](https://docs.microsoft.com/windows-hardware/drivers/kernel/using-i-o-control-codes) in the *Kernel Mode Architecture Guide* and "Device Input and Output Control Codes" in the Microsoft Windows SDK documentation. (This resource may not be available in some languages and countries.)

**Neither**  
Union component used for IRP_MN_KERNEL_CALL and IRP_MN_USER_FS_REQUEST operations when the buffering method is METHOD_NEITHER. For more information about buffering methods, see [Defining I/O Control Codes](https://docs.microsoft.com/windows-hardware/drivers/kernel/defining-i-o-control-codes) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**InputBuffer**  
User-mode virtual address of the input buffer that the original requester of the operation supplied. The I/O Manager and Filter Manager do not validate these addresses. To ensure that user-space addresses are valid, the minifilter must use routines such as [**ProbeForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforread), [**ProbeForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforwrite), and [**MmProbeAndLockPages**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmprobeandlockpages), enclosing all buffer references in **try/except** blocks. For more information, see [Using Neither Buffered Nor Direct I/O](https://docs.microsoft.com/windows-hardware/drivers/kernel/using-neither-buffered-nor-direct-i-o) and [Errors in Referencing User-Space Addresses](https://docs.microsoft.com/windows-hardware/drivers/kernel/errors-in-referencing-user-space-addresses) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**OutputBuffer**  
User-mode virtual address of the output buffer that the original requester of the operation supplied. The I/O Manager and Filter Manager do not validate these addresses. To ensure that user-space addresses are valid, the minifilter must use routines such as [**ProbeForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforread), [**ProbeForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforwrite), and [**MmProbeAndLockPages**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmprobeandlockpages), enclosing all buffer references in **try/except** blocks. For more information, see [Using Neither Buffered Nor Direct I/O](https://docs.microsoft.com/windows-hardware/drivers/kernel/using-neither-buffered-nor-direct-i-o) and [Errors in Referencing User-Space Addresses](https://docs.microsoft.com/windows-hardware/drivers/kernel/errors-in-referencing-user-space-addresses) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**Neither.OutputBuffer** is optional and can be NULL if a MDL is provided in **Neither.OutputMdlAddress**. See **Remarks**.

**OutputMdlAddress**  
Address of a memory descriptor list (MDL) that describes the buffer that the **Neither.OutputBuffer** member points to. This member is optional and can be **NULL** if a buffer is provided in **Neither.OutputBuffer**.

**Buffered**  
Union component used for IRP_MN_KERNEL_CALL and IRP_MN_USER_FS_REQUEST operations when the buffering method is METHOD_BUFFERED. For more information about buffering methods, see [Defining I/O Control Codes](https://docs.microsoft.com/windows-hardware/drivers/kernel/defining-i-o-control-codes) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**SystemBuffer**  
Address of the system-allocated buffer for the operation. In METHOD_BUFFERED I/O, this buffer is used for both input and output. For more information, see [Methods for Accessing Data Buffers](https://docs.microsoft.com/windows-hardware/drivers/kernel/methods-for-accessing-data-buffers) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**Direct**  
Union component used for IRP_MN_KERNEL_CALL and IRP_MN_USER_FS_REQUEST operations when the buffering method is METHOD_IN_DIRECT or METHOD_OUT_DIRECT. For more information about buffering methods, see [Defining I/O Control Codes](https://docs.microsoft.com/windows-hardware/drivers/kernel/defining-i-o-control-codes) in the *Kernel Mode Architecture Guide*.

**InputSystemBuffer**  
Address of the input buffer for the operation. This buffer is locked down by the operating system so that it is safe to access from kernel mode. For more information, see [Methods for Accessing Data Buffers](https://docs.microsoft.com/windows-hardware/drivers/kernel/methods-for-accessing-data-buffers) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**OutputBuffer**  
User-mode virtual address of the output buffer that the original requester of the operation supplied. In direct I/O, unlike METHOD_NEITHER I/O, the operating system locks down this buffer so that it is safe to access from kernel mode, as long as the minifilter is in the same process context as the original requester of the I/O operation. (Otherwise it must call [**MmGetSystemAddressForMdlSafe**](https://docs.microsoft.com/windows-hardware/drivers/kernel/mm-bad-pointer) to get the system address from the MDL that the **OutputMdlAddress** member points to.) For more information, see [Using Direct I/O](https://docs.microsoft.com/windows-hardware/drivers/kernel/using-direct-i-o) and [Errors in Direct I/O](https://docs.microsoft.com/windows-hardware/drivers/kernel/errors-in-direct-i-o) in the *Kernel Mode Architecture Guide*. (This resource may not be available in some languages and countries.)

**OutputMdlAddress**  
Address of a memory descriptor list (MDL) that describes the buffer that the **Direct.OutputBuffer** member points to. This member is required and cannot be **NULL**.

## Remarks

The [**FLT_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters) structure for [**IRP_MJ_FILE_SYSTEM_CONTROL**](irp-mj-file-system-control.md) operations contains the parameters for a file-system-control-information operation represented by a callback data ([**FLT_CALLBACK_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)) structure. It is contained in an [**FLT_IO_PARAMETER_BLOCK**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block) structure.

If both a **Neither.OutputBuffer** and **Neither.MdlAddress** buffer are provided, it is recommended that minifilters use the MDL.

If a minifilter changes the value of **Neither.MdlAddress**, then after its post operation callback, Filter Manager will free the MDL currently stored in **Neither.MdlAddress** and restore the previous value of **Neither.MdlAddress**.

IRP_MJ_FILE_SYSTEM_CONTROL is an IRP-based operation.

## Requirements

|   |   |
| - | - |
| Header | Fltkernel.h (include Fltkernel.h) |

## See also

[**FLT_CALLBACK_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)

[**FLT_IO_PARAMETER_BLOCK**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block)

[**FLT_IS_FASTIO_OPERATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)

[**FLT_IS_FS_FILTER_OPERATION**](https://docs.microsoft.com/previous-versions/ff544648(v=vs.85))

[**FLT_IS_IRP_OPERATION**](https://docs.microsoft.com/previous-versions/ff544654(v=vs.85))

[**FLT_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters)

[**FltFsControlFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfscontrolfile)

[**IoBuildAsynchronousFsdRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iobuildasynchronousfsdrequest)

[**IoBuildSynchronousFsdRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iobuildsynchronousfsdrequest)

[**IoVerifyVolume**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ioverifyvolume)

[**IRP_MJ_FILE_SYSTEM_CONTROL**](irp-mj-file-system-control.md)

[**MmGetSystemAddressForMdlSafe**](https://docs.microsoft.com/windows-hardware/drivers/kernel/mm-bad-pointer)

[**MmProbeAndLockPages**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmprobeandlockpages)

[**ProbeForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforread)

[**ProbeForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforwrite)

[**ZwFsControlFile**](https://msdn.microsoft.com/library/windows/hardware/ff566462)
