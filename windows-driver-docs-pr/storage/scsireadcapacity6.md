---
title: ScsiReadCapacity
description: ScsiReadCapacity
ms.assetid: ee4a0d3f-028b-4d25-badf-393198da3191
ms.localizationpriority: medium
ms.date: 10/17/2018
---

# ScsiReadCapacity


The **ScsiReadCapacity** method instructs the miniport driver that manages an iSCSI initiator HBA to log on to the target and issue a SCSI read capacity command to a logical unit on the target and then return the results.

This WMI method belongs to the unpublished [MSiSCSI\_Operations WMI Class](msiscsi-operations-wmi-class.md). For a description of the parameters of the **ScsiReadCapacity** method, see the member descriptions for the [**ScsiReadCapacity\_IN**](https://docs.microsoft.com/windows-hardware/drivers/ddi/iscsiop/ns-iscsiop-_scsireadcapacity_in) and [**ScsiReadCapacity\_OUT**](https://docs.microsoft.com/windows-hardware/drivers/ddi/iscsiop/ns-iscsiop-_scsireadcapacity_out) structures.

Miniport drivers that implement the MSiSCSI\_Operations WMI class must support **ScsiReadCapacity**.

 

 





