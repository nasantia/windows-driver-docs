---
title: FLT_PARAMETERS for IRP_MJ_WRITE union
description: The following union component is used when the MajorFunction field of the FLT_IO_PARAMETER_BLOCK structure for the operation is IRP_MJ_WRITE.
ms.assetid: c40d4c9e-2d09-4cd1-9278-5067dad2914f
keywords: ["FLT_PARAMETERS for IRP_MJ_WRITE union Installable File System Drivers", "FLT_PARAMETERS union Installable File System Drivers", "PFLT_PARAMETERS union pointer Installable File System Drivers"]
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

# FLT_PARAMETERS for IRP_MJ_WRITE union

The following union component is used when the **MajorFunction** field of the [**FLT_IO_PARAMETER_BLOCK**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block) structure for the operation is [**IRP_MJ_WRITE**](irp-mj-write.md).

## Syntax

```ManagedCPlusPlus
typedef union _FLT_PARAMETERS {
  ...    ;
  struct {
    ULONG         Length;
    ULONG         Key;
    LARGE_INTEGER ByteOffset;
    PVOID         WriteBuffer;
    PMDL          MdlAddress;
  } Write;
  ...    ;
} FLT_PARAMETERS, *PFLT_PARAMETERS;
```

## Members

**Write**  
Structure containing the following members.

**Length**  
Length, in bytes, of the data to be written.

**Key**  
Key value associated with a byte-range lock on the target file.

**ByteOffset**  
Starting byte offset within the file of the data to be written.

**WriteBuffer**  
Pointer to a buffer that contains the data to be written to the file. This member is optional and can be NULL if a MDL is provided in **MdlAddress**. See **Remarks**.

**MdlAddress**  
Address of a memory descriptor list (MDL) that describes the buffer that the **WriteBuffer** member points to. This member is optional and can be **NULL** if a buffer is provided in **WriteBuffer**. See **Remarks**.

## Remarks

The [**FLT_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters) structure for IRP_MJ_WRITE operations contains the parameters for a write operation represented by a callback data ([**FLT_CALLBACK_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)) structure. It is contained in an FLT_IO_PARAMETER_BLOCK structure.

If both a **WriteBuffer** and **MdlAddress** buffer are provided, it is recommended that minifilters use the MDL. The memory that **WriteBuffer** points to is valid when it is a user mode address being accessed within the context of the calling process, or if it is a kernel mode address.

If a minifilter changes the value of **MdlAddress**, then after its post operation callback, Filter Manager will free the MDL currently stored in **MdlAddress** and restore the previous value of **MdlAddress**.

IRP_MJ_WRITE can be an IRP-based operation or a fast I/O operation.

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

[**FltWriteFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltwritefile)

[**IRP_MJ_WRITE**](irp-mj-write.md)

[**ZwWriteFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntwritefile)
