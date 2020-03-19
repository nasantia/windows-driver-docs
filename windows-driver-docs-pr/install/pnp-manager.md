---
title: Plug and Play Manager
description: Plug and Play Manager
ms.assetid: b1890b3c-fc7b-4a2e-b48a-8266f237c9b6
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Plug and Play Manager


The Plug and Play (PnP) manager provides the support for PnP functionality in Windows and is responsible for the following PnP-related tasks:

-   Device detection and enumeration while the system is booting

-   Adding or removing devices while the system is running

The kernel-mode PnP manager notifies the user-mode PnP manager that a new device is present on the system and must be installed.

The kernel-mode PnP manager also calls the [*DriverEntry*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize) and [*AddDevice*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_add_device) routines of a device's driver and sends the [**IRP_MN_START_DEVICE**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-start-device) request to start the device.

The PnP manager maintains the [Device Tree](https://docs.microsoft.com/windows-hardware/drivers/kernel/device-tree) that keeps track of the devices in the system. The device tree contains information about the devices present on the system. When the computer starts, the PnP manager builds this tree by using information from drivers and other components, and updates the tree as devices are added or removed.

 

 





