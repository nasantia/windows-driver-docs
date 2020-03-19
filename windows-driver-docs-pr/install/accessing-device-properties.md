---
title: Accessing Device Properties
description: Accessing Device Properties
ms.assetid: 7D3F3164-E530-49fb-BCCD-9C024543FA95
keywords:
- device properties WDK device installations , accessing
- accessing device properties WDK device installations
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Accessing Device Properties


You must not discover or change [device properties](device-properties.md) by directly accessing registry keys. Registry keys do not contain required information to discover or change device properties. In addition, the location, format, and meaning of these keys might change between different versions of Windows.

The [SetupAPI](setupapi.md) functions provide consistent behavior and enforce access permissions to protect device properties. Starting with Windows Vista, device properties that have restricted write access also have restricted read access.

To safely access device properties, follow these guidelines:

-   For user-mode applications, follow these steps:

    1.  Starting with Windows Vista, use [**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw) to retrieve device properties, and use [**SetupDiSetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdevicepropertyw) with DEVPKEY_Xxx property codes to set device properties.

        For more information about device instance properties on Windows Vista and later versions of Windows, see [Accessing Device Instance Properties (Windows Vista and Later)](accessing-device-instance-properties--windows-vista-and-later-.md).

        **Note**  Starting with Windows Vista, some device properties are reserved by the operating system. For more information, see [Modifying Device Properties](modifying-device-properties.md).

    2.  On Windows 2000, Windows XP, and Windows Server 2003, use [**SetupDiGetDeviceRegistryProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacepropertyw) to retrieve device properties, and use [**SetupDiSetDeviceRegistryProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceregistrypropertya) with SPDRP_Xxx property codes to set device properties.

        For more information about device instance properties on Windows 2000, Windows XP, and Windows Server 2003, see [Accessing Device Instance SPDRP_Xxx Properties](accessing-device-instance-spdrp-xxx-properties.md).

    3.  Use persistent storage within the registry for custom settings of devices that are physically present and for those that are not. In this case, you must create your own set of registry keys and values. To do this, use **SetupDiCreateDevRegKey** (DIREG_DEV) or *software key* (DIREG_DRV) for the device.

        **Note**  Hardware keys persist in the registry until the device is uninstalled. Software keys can be moved or cleared by the [device installation components](https://docs.microsoft.com/previous-versions/ff541277(v=vs.85)) during a driver upgrade

        To save the custom settings, use [RegCloseKey](https://go.microsoft.com/fwlink/p/?linkid=194543) after the registry key has been created or opened.

-   For kernel-mode drivers, use [**IoGetDeviceProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetdeviceproperty) to access device properties.

 

 





