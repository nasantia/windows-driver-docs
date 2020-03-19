---
title: Creating Device Objects in a Filter Driver
description: Creating Device Objects in a Filter Driver
ms.assetid: f5a4851d-7caf-467d-9500-11f341fdf680
keywords:
- PnP WDK KMDF , filter drivers
- Plug and Play WDK KMDF , filter drivers
- power management WDK KMDF , filter drivers
- filter drivers WDK KMDF
- filter DOs WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Creating Device Objects in a Filter Driver


Each [filter driver](https://docs.microsoft.com/windows-hardware/drivers/kernel/filter-drivers) creates a framework device object for each of its supported devices that exists on the system. Because these device objects are created by filter drivers, they are called filter device objects (Filter DOs). Each Filter DO is a filter driver's representation of a device.

Filter drivers, like function drivers, provide an [*EvtDriverDeviceAdd*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/nc-wdfdriver-evt_wdf_driver_device_add) callback function that receives a handle to a [**WDFDEVICE\_INIT**](https://docs.microsoft.com/windows-hardware/drivers/wdf/wdfdevice_init) structure. The driver can call the same set of [framework device object initialization methods](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/#device-init-methods) that function drivers call to store information in the WDFDEVICE\_INIT structure. Like function drivers, filter drivers can also call [framework FDO initialization methods](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/#fdo-init-methods).

A small number of filter drivers enumerate child software-only devices. Such filter drivers can call [framework PDO initialization methods](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/#pdo-init-methods).

Filter drivers must call [**WdfFdoInitSetFilter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nf-wdffdo-wdffdoinitsetfilter).

The final step in creating a device object is to call [**WdfDeviceCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicecreate).

 

 





