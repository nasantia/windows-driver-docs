---
title: Storage Filter Driver's AddDevice Routine
description: Storage Filter Driver's AddDevice Routine
ms.assetid: 7970fb3e-4e4c-4ff7-9738-e09454a864c4
keywords:
- storage filter drivers WDK , AddDevice
- filter drivers WDK storage , AddDevice
- SFD WDK storage , AddDevice
- AddDevice routine WDK storage
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Storage Filter Driver's AddDevice Routine

The PnP manager calls the [*AddDevice*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_add_device) routine of a storage filter driver when it detects a device controlled by that driver. The *AddDevice* routine of an storage filter driver (SFD) is similar to that of a storage class driver, except that it must not attempt to claim the device (SRB_FUNCTION_CLAIM_DEVICE).

For information about a storage class driver's [*AddDevice*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_add_device) routine, see [Storage Class Drivers](introduction-to-storage-class-drivers.md). For general information about a PnP driver's *AddDevice* routine, see [Plug and Play](https://docs.microsoft.com/windows-hardware/drivers/kernel/implementing-plug-and-play).
