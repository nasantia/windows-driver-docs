---
title: Accessing Kernel-Mode Drivers for Still Image Devices
description: Accessing Kernel-Mode Drivers for Still Image Devices
ms.assetid: f9216d3c-4930-4c26-8eac-6ee500b038e0
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Accessing Kernel-Mode Drivers for Still Image Devices





Microsoft provides WDM-based kernel-mode drivers to support still image devices connected to SCSI and USB buses. Both drivers support Plug and Play devices and provide services for adding, removing, starting, stopping, and creating registry entries for Plug and Play devices. Additionally, both drivers provide suspend and resume operations for devices that support power management.

User-mode still image minidrivers can access these kernel-mode drivers by calling [**CreateFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-createfilea), **ReadFile**, **WriteFile**, and [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) (described in the Microsoft Windows SDK documentation). **ReadFile** and **WriteFile** are used for block data transfers. Specifically, **ReadFile** is called to obtain image data, and **WriteFile** is used for sending commands to devices that accept commands as data streams.

Before calling **ReadFile**, **Writefile** or [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol), the minidriver must call [**IStiDeviceControl::GetMyDevicePortName**](https://docs.microsoft.com/windows-hardware/drivers/ddi/stiusd/nf-stiusd-istidevicecontrol-getmydeviceportname) to obtain the device's port name and then use that port name as a parameter to [**CreateFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-createfilea).

[SCSI Driver](scsi-driver.md)

[USB Driver](usb-driver.md)

 

 




