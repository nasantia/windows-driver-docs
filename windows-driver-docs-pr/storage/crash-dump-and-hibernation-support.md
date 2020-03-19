---
title: Crash Dump and Hibernation Support
description: Crash Dump and Hibernation Support
ms.assetid: 6f5e6f4e-b734-45fe-80d5-fd7b81c9b329
keywords:
- crash dump WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Crash Dump and Hibernation Support


A Storport virtual miniport driver must support the [**SCSI\_REQUEST\_BLOCK**](https://docs.microsoft.com/windows-hardware/drivers/ddi/srb/ns-srb-_scsi_request_block) (SRB) function code SRB\_FUNCTION\_DUMP\_POINTERS. When a miniport driver receives this type of SRB, the DataBuffer SRB member points to a [**MINIPORT\_DUMP\_POINTERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/storport/ns-storport-_miniport_dump_pointers) structure. This SRB is sent to a virtual miniport driver that is used to control the disk that holds the crash dump data after the SRB returns from the miniport driver's [**HwStorInitialize**](https://docs.microsoft.com/windows-hardware/drivers/ddi/storport/nc-storport-hw_initialize) routine.

 

 




