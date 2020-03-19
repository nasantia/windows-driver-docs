---
title: Device identification strings
description: The Plug and Play (PnP) manager and other device installation components use device identification strings to identify devices that are installed in a computer.
ms.assetid: dae23185-63d9-4a0f-9786-c7fa66368826
keywords:
- compatible IDs WDK device installations
- device IDs WDK device installations
- device instance IDs WDK device installations
- driver nodes WDK device installations
- hardware IDs WDK device installations
- instance IDs WDK device installations
- Device setup WDK device installations , device identification strings
- device installations WDK , device identification strings
- installing devices WDK , device identification strings
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Device Identification Strings

The Plug and Play (PnP) manager and other [device installation components](https://docs.microsoft.com/windows-hardware/drivers/install/overview-of-device-and-driver-installation) use device identification strings to identify devices that are installed in a computer.

Windows uses the following device identification strings to locate the information (INF) file that best matches the device. These strings are reported by a device's enumerator, a system component that discovers PnP devices based on a PnP hardware standard. These tasks are carried out by PnP Bus Drivers in partnership with the PnP manager. A device is typically enumerated by its parent bus driver, such as the PCI or PCMCIA bus driver. Some devices are enumerated by a bus filter driver, such as the ACPI Driver.

- [Hardware IDs](hardware-ids.md)

- [Compatible IDs](compatible-ids.md)

Windows tries to find a match for one of the hardware IDs or compatible IDs. For more information about how Windows uses these IDs to match a device to an INF file, and how to specify IDs in an INF file, see [How Windows Selects Drivers](how-setup-selects-drivers.md).

In addition to using the preceding IDs to identify devices, the PnP manager uses the following IDs to uniquely identify instances of each device that are installed in a computer:

- [Instance IDs](instance-ids.md)

- [Device instance IDs](device-instance-ids.md)

Starting with Windows 7, the PnP manager uses the [Container ID](container-ids.md) device identification string to group one or more device nodes (devnodes) that were enumerated from each instance of a physical device installed in a computer.

Each enumerator customizes its device IDs, hardware IDs, and compatible IDs to uniquely identify the device that it enumerates. In addition, each enumerator has its own policy to identify hardware IDs and compatible IDs. For more information about hardware ID and compatible ID formats for most of the system buses, see [Device Identifier Formats](device-identifier-formats.md).

> [!NOTE]
> Device identification strings should not be parsed. They are meant only for string comparisons and should be treated as opaque strings.

