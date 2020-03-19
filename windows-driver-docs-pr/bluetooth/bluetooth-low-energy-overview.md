---
title: Bluetooth Low Energy Overview
description: This section provides an overview of Bluetooth Low Energy introduced in Windows 8
ms.assetid: 8783E31B-99A3-40EB-8A67-647AFAB7D4D3
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Bluetooth Low Energy Overview


Windows 8 introduces support for the Bluetooth Low Energy technology.

Bluetooth Low Energy introduces a new physical layer that shares the same frequency space as Bluetooth Basic Rate. Profiles that are developed on this technology are organized into the Generic Attribute Profile (or GATT).

Each profile defines the use of one or more services to create a use case or scenario. Compliant service implementations are constructed from characteristics organized in a way that conforms to the established schema defined on the Bluetooth Special Interest Group [developer website](https://www.bluetooth.com/specifications/gatt/services/).

The diagram below illustrates the way objects are structured inside a typical GATT service.

![bluetooth low energy gatt service declarations](images/bthleservicedeclaration.png)

When a Bluetooth Low Energy device is paired with a Windows 8 machine, the device becomes part of the system and Windows will provide device objects to represent both the device and the primary services reported by the device.

![device object structure of the windows 8 bluetooth low energy implementation](images/bthlewin8supt.png)

Each device and its primary services are represented as device objects in Windows and these device objects can be queried and managed using the [device installation functions](https://docs.microsoft.com/previous-versions/ff549791(v=vs.85)) such as [**SetupDiEnumDeviceInfo**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdeviceinfo), and [**SetupDiGetDeviceProperty**](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw).

In addition to the standard [Bluetooth Profile Driver functions](https://docs.microsoft.com/windows-hardware/drivers/ddi/index), Windows 8 introduces new [Bluetooth Low Energy functions](https://docs.microsoft.com/windows-hardware/drivers/ddi/index) which allows for the development of Bluetooth GATT client applications.

These functions allows for the enumeration of services and their objects (including services, characteristics and their descriptors) as well as read and write capabilities.

 

 





