---
title: Human interface devices (HID) driver samples
description: The driver samples in this directory provide a starting point for writing a custom HID driver for your device.
ms.assetid: 38C52EAD-9DC6-4575-A9FF-1472FDDC2702
ms.date: 11/19/2019
ms.localizationpriority: medium
---

# Human interface devices (HID) driver samples

The driver samples in this directory provide a starting point for writing a custom HID driver for your device.

| Sample | Description |
| --- | --- |
| [KMDF HID Filter](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/kmdf-filter-driver-for-a-hid-device) | A filter driver for a HID device. Along with illustrating how to write a filter driver, this sample shows how to use remote I/O target interfaces to open a HID collection in kernel-mode and send IOCTL requests to set and get feature reports, as well as how an application can use WMI interfaces to send commands to a filter driver. |
| [HClient Application](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/hclient-sample-application) | Demonstrates how to write a user-mode client application that communicates with HID devices conforming to the HID device class specification. |
| [HIDUSBFX2](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/hidusbfx2-sample-driver) | Demonstrates mapping of a non-HID USB device to a HID device. |
| [UMDF HID Minidriver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/hid-minidriver-sample-umdf-version-2) | A sample demonstrating how to write a HID minidriver using the User-Mode Driver Framework (UMDF).
