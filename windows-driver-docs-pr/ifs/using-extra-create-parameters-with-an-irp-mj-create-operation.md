---
title: Extra Create Parameters
description: Extra Create Parameters
ms.assetid: e32aeec6-1a0a-4d21-8358-89d9fc0a15eb
ms.date: 10/16/2019
ms.localizationpriority: medium
---

# Extra Create Parameters

Extra create parameters (ECPs) are structures that can contain additional information for file creates. A create operation can have any number of ECPs, which are attached using an ECP_LIST. Operating system components use ECPs to associate additional information with the [**IRP_MJ_CREATE**](https://docs.microsoft.com/windows-hardware/drivers/ifs/irp-mj-create) operation on a file.

Drivers can also use ECPs to process or associate additional information with the IRP_MJ_CREATE operation on a file in the following situations:

- When a kernel-mode driver calls the [**FltCreateFileEx2**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcreatefileex2) or [**IoCreateFileEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-iocreatefileex) routine to create or open the file

- When a file system filter driver processes the [**IRP_MJ_CREATE**](https://docs.microsoft.com/windows-hardware/drivers/ifs/irp-mj-create) operation for the file

The following sections describe how to define, attach, and use ECPs, and describes operating system-defined ECPs.

[Attaching ECPs to IRP_MJ_CREATE Operations that a Kernel-Mode Driver Originated](attaching-ecps-to-irp-mj-create-operations-that-a-kernel-mode-driver-o.md)

[Using ECPs to Process IRP_MJ_CREATE Operations in a File System Minifilter Driver](using-ecps-to-process-irp-mj-create-operations-in-a-file-system-minifilter.md)

[User-Defined ECPs](user-defined-ecps.md)

[System-Defined ECPs](system-defined-ecps.md)
