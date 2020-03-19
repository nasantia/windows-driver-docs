---
title: Power-up sequence for a NetAdapterCx client driver
description: Power-up sequence for a NetAdapterCx client driver
ms.assetid: 86694F6B-9AE4-4FDB-A4BB-9B7ACBC0B1DA
keywords:
- Power-up sequence for a NetAdapterCx client driver, Power-up sequence for a NetAdapterCx client driver, Power-up sequence for a NetCx client driver
ms.date: 08/07/2018
ms.localizationpriority: medium
---

# Power-up sequence for a NetAdapterCx client driver

The following figure shows the order in which NetAdapterCx calls a client driver's event callback functions when bringing a device to the fully operational state, starting from the Device Arrived state at the bottom of the figure:

<img src="images/netadaptercx-powerup.png" alt="Device enumeration and power-up sequence for NetAdapterCx client driver" title="Device enumeration and power-up sequence for NetAdapterCx client driver" style="width: 600px;"/>

The broad horizontal lines mark the steps that are involved in starting a device. The column on the left side of the figure describes the step, and the column on the right lists the event callbacks that accomplish it. Steps marked with blue text are specific to NetAdapterCx, while other steps are common to all WDF-based drivers.

At the bottom of the figure, the device is not present on the system. When the user inserts the device, the framework begins by calling the driver’s [*EvtDriverDeviceAdd*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/nc-wdfdriver-evt_wdf_driver_device_add) callback so that the driver can create a device object to represent the device. The framework continues calling the driver's callback routines by progressing up through the sequence until the device is operational. Remember that the framework invokes the event callbacks in bottom-up order as shown in the figure, so [*EvtDeviceFilterRemoveResourceRequirements*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nc-wdffdo-evt_wdf_device_filter_resource_requirements) is called before [*EvtDeviceFilterAddResourceRequirements*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nc-wdffdo-evt_wdf_device_filter_resource_requirements) and so on. If the device was stopped to rebalance resources or was physically present but in a low-power state, not all of the steps are required, as the figure shows.

