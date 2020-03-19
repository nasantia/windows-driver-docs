---
title: Handling PnP Start in a Storage Filter Driver
description: Handling PnP Start in a Storage Filter Driver
ms.assetid: 02a87fec-772d-4416-bd3a-5c7f98e8d55e
keywords:
- storage filter drivers WDK , PnP
- filter drivers WDK storage , PnP
- SFD WDK storage , PnP
- PnP WDK storage
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Handling PnP Start in a Storage Filter Driver

A storage filter driver (SFD) performs device-specific initialization and sets up its device extension when the PnP manager calls its [*DispatchPnP*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_dispatch) routine with a start request ([**IRP\_MJ\_PNP**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mj-pnp) with [**IRP\_MN\_START\_DEVICE**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-start-device)). An SFD handles a start request in much the same way as does a storage class driver.

For information about how a storage class driver handles a start request and sets up its device extension, see [Storage Class Drivers](introduction-to-storage-class-drivers.md). For general information about handling a PnP start request, see [Plug and Play](https://docs.microsoft.com/windows-hardware/drivers/kernel/implementing-plug-and-play).
