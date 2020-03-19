---
title: Accessing the Unified Device Property Model
description: This topic describes how a Windows Driver Frameworks (WDF) driver retrieves or modifies properties that are exposed through the unified device property model.
ms.assetid: C81988F9-E0DA-439F-B770-DAD86E33D5F3
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Accessing the Unified Device Property Model


This topic describes how a Windows Driver Frameworks (WDF) driver retrieves or modifies properties that are exposed through the unified device property model. The methods listed are available starting in User-Mode Driver Framework (UMDF) version 2.0 and Kernel-Mode Driver Framework (KMDF) version 1.13.

Both KMDF and UMDF drivers can call the following methods:

-   [**WdfDeviceAllocAndQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceallocandquerypropertyex)
-   [**WdfDeviceAssignProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceassignproperty)
-   [**WdfDeviceQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicequerypropertyex)

Both KMDF and UMDF drivers can call the following methods only before calling [**WdfDeviceCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicecreate). For more information about calling **WdfDeviceCreate**, see [Creating a Framework Device Object](creating-a-framework-device-object.md).

After calling [**WdfDeviceCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicecreate), a driver can obtain device property information by calling the corresponding **WdfDevice*Xxx*Property** method.

-   [**WdfFdoInitAllocAndQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nf-wdffdo-wdffdoinitallocandquerypropertyex)
-   [**WdfFdoInitQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nf-wdffdo-wdffdoinitquerypropertyex)

The *-Ex* methods above differ from their non*-Ex* counterparts in that they allow you to specify properties using the [**WDF\_DEVICE\_PROPERTY\_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/ns-wdfdevice-_wdf_device_property_data) structure, instead of the subset that you can specify using [**DEVICE\_REGISTRY\_PROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfwdm/ne-wudfwdm-device_registry_property).

Before receiving device property data, drivers typically call **Wdf*Xxx*QueryProperty** just to obtain the required buffer size. For some properties, the data size can change between when the required size is returned and when the driver calls **Wdf*Xxx*QueryProperty** again. Therefore, drivers should call **Wdf*Xxx*QueryProperty** inside a loop that executes until the return status is not **STATUS\_BUFFER\_TOO\_SMALL**.

It is best to use **Wdf*Xxx*QueryProperty** only if the required buffer size is known and unchanging, because in that case the driver has to call **Wdf*Xxx*QueryProperty** only once. If the required buffer size is unknown or varies, the driver should call **Wdf*Xxx*AllocAndQueryProperty**.

## Accessing Device Interface Properties


UMDF drivers can use the following methods to retrieve or modify [device interface properties](https://docs.microsoft.com/previous-versions/ff541409(v=vs.85)) that are exposed through the unified property model:

-   [**WdfDeviceAllocAndQueryInterfaceProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceallocandqueryinterfaceproperty)
-   [**WdfDeviceAssignInterfaceProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceassigninterfaceproperty)
-   [**WdfDeviceQueryInterfaceProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicequeryinterfaceproperty)

To retrieve or modify a device interface property, a KMDF driver must call [**IoGetDeviceInterfacePropertyData**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetdeviceinterfacepropertydata) or [**IoSetDeviceInterfacePropertyData**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iosetdeviceinterfacepropertydata) directly.

 

 





