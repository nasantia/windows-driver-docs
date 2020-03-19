---
title: Windows Portable Device (WPD) driver samples
description: The driver samples in this directory provide a starting point for writing a custom WPD driver for your device.
ms.assetid: 5EB5B820-A29A-4A93-BBB9-6F4CDF101E3B
ms.date: 11/21/2019
ms.localizationpriority: medium
---

# Windows Portable Device (WPD) driver samples

The driver samples in this directory provide a starting point for writing a custom WPD driver for your device.

| Sample | Description |
| --- | --- |
| [WPD Basic Hardware Sample Driver (UMDF 1)](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wpd-basic-hardware-sample-driver-umdf-version-1)  | A WPD sample driver that supports nine sensor devices that integrate with the Parallax BS2 programmable microcontroller. |
| [Hello World Example](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wpdhelloworld-sample-driver-for-portable-devices) | This sample driver supports four objects: a device object, a storage object, a folder object, and a file object. Each object supports a set of properties. |
| [Multi-transport driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wpd-multi-transport-sample-driver) | Demonstrates how you could extend the WpdHelloWorldDriver for a device that supports multiple transports. A transport is a protocol over which a portable device communicates with a computer. Example transports include Internet Protocol (IP), Bluetooth, and USB. |
| [WPD service sample driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wpd-service-sample-driver) | Demonstrates how to extend the WpdHelloWorldDriver sample so that it supports a simulated device with a Contacts device service. |
| [WUDF driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wpd-wudf-sample-driver) | A comprehensive WPD sample driver demonstrates virtually all aspects of the WPD device driver interface (DDI). |
