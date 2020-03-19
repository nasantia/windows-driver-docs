---
title: Overview of Boot Options in Windows
description: Describes Windows boot loader architecture, firmware-independent boot configuration, and boot option editing tool.
ms.assetid: 1cc5b1cc-8d0e-4b4e-93fe-272772a3e458
keywords:
- boot options WDK , Windows
- editing boot options
- multiboot systems WDK boot options
- legacy boot entries WDK
- Boot Configuration Data WDK
- BCD WDK
- BCDEdit tool
- boot options WDK , editing
- ntldr tool
- Windows Boot Manager WDK
- Bootmgr tool
- system-specific boot loaders WDK
- boot loaders WDK
- firmware-independent boot options WDK
ms.date: 04/23/2019
ms.localizationpriority: medium
---

# Overview of Boot Options in Windows

The Windows boot loader architecture includes a firmware-independent boot configuration and storage system called *Boot Configuration Data* (BCD) and a boot option editing tool, BCDEdit (BCDEdit.exe). During development, you can use BCDEdit to configure boot options for debugging, testing, and troubleshooting your driver on computers running Windows 10, Windows 8, Windows Server 2012, Windows 7, and Windows Server 2008.

> [!CAUTION]
> Administrative privileges are required to use BCDEdit to modify BCD. Changing some boot entry options using BCDEdit could render your computer inoperable. As an alternative, use the System Configuration utility (MSConfig.exe) to change boot settings.

## Boot Loading Architecture

Windows includes boot loader components that are designed to load Windows quickly and securely. The previous Windows NT boot loader, *ntldr*, is replaced by three components:

- Windows Boot Manager (Bootmgr.exe)

- Windows operating system loader (Winload.exe)

- Windows resume loader (Winresume.exe)

In this configuration, the Windows Boot Manager is generic and unaware of the specific requirements for each operating system while the system-specific boot loaders are optimized for the system that they load.

When a computer with multiple boot entries includes at least one entry for Windows, the Windows Boot Manager, which resides in the root directory, starts the system and interacts with the user. It displays the boot menu, loads the selected system-specific boot loader, and passes the boot parameters to the boot loader.

The boot loaders reside in the root directory of each Windows partition. Once selected, the boot loaders take over the boot process and load the operating system in accordance with the selected boot parameters.

## Boot Configuration Data

Windows boot options are stored in the Boot Configuration Data (BCD) store on BIOS-based and EFI-based computers.


BCD provides a common, firmware-independent boot option interface for all computers running Windows 10, Windows 8, Windows Server 2012, Windows 7, and Windows Server 2008. It is more secure than previous boot option storage configurations, because it permits secure lockdown of the BCD store and lets Administrators assign rights for managing boot options. BCD is available at run time and during all phases of setup. You can even call BCD during power state transitions and use it to define the boot process for resuming after hibernation.

You can manage BCD remotely and manage BCD when the system boots from media other than the media on which the BCD store resides. This feature is extremely important for debugging and troubleshooting, especially when a BCD store must be restored while running Startup Repair from a DVD, from USB-based storage media, or even remotely.

The BCD store, with its familiar object-and-element architecture, uses GUIDs and names such as "Default" to precisely identify boot-related applications.

BCD includes its own set of boot options. For more information about these boot options, see [BCD Boot Options Reference](https://docs.microsoft.com/windows-hardware/drivers/ddi/index).

## Editing Boot Options

To edit boot options in Windows, use BCDEdit (BCDEdit.exe), a tool included in Windows. 

To use BCDEdit, you must be a member of the Administrators group on the computer.

You can also use the System Configuration utility (MSConfig.exe) to change boot settings.

To change boot options programmatically in Windows, use the Windows Management Instrument (WMI) interface to boot options. This BCD WMI interface is the best method to programmatically change the boot options. For information about the BCD WMI interface, see [Boot Configuration Data WMI Provider](https://docs.microsoft.com/previous-versions/windows/desktop/bcd/boot-configuration-data-portal) in the Windows SDK documentation.

## Related topics

- [BCD Edit Options Reference](bcd-boot-options-reference.md)
- [Editing Boot Options](editing-boot-options.md)
- [Using Boot Parameters](using-boot-parameters.md)

