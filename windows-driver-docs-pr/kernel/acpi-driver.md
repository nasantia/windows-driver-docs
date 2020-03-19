---
title: Acpi.sys The Windows ACPI Driver
description: The Windows ACPI driver, Acpi.sys, is an inbox component of the Windows operating system.
ms.assetid: 38ca54e0-defe-48b2-ab00-a5f688c2eb01
keywords: ["ACPI drivers WDK power management", "enumerators WDK power management", "PDOs WDK power management", "filter DOs WDK power management", "physical device objects WDK power management"]
ms.date: 06/16/2017
ms.localizationpriority: High
---

# Acpi.sys: The Windows ACPI Driver


The Windows ACPI driver, Acpi.sys, is an inbox component of the Windows operating system. The responsibilities of Acpi.sys include support for power management and Plug and Play (PnP) device enumeration. On hardware platforms that have an [ACPI BIOS](acpi-bios.md), the [HAL](windows-kernel-mode-hal-library.md) causes Acpi.sys to be loaded during system startup at the base of the [device tree](device-tree.md). Acpi.sys acts as the interface between the operating system and the ACPI BIOS. Acpi.sys is transparent to the other drivers in the device tree.

Other tasks performed by Acpi.sys on a particular hardware platform might include reprogramming the resources for a COM port or enabling the USB controller for system wake-up.

**In this topic**

-   [ACPI devices](#acpi-devices)
-   [ACPI control methods](#acpi-control-methods)
-   [ACPI specification](#acpi-specification)
-   [ACPI debugging](#acpi-debugging)

## ACPI devices


The hardware platform vendor specifies a hierarchy of ACPI namespaces in the ACPI BIOS to describe the hardware topology of the platform. For more information, see [ACPI Namespace Hierarchy](https://docs.microsoft.com/windows-hardware/drivers/bringup/acpi-namespace-hierarchy).

For each device described in the ACPI namespace hierarchy, the Windows ACPI driver, Acpi.sys, creates either a filter device object (filter DO) or a physical device object (PDO). If the device is integrated into the system board, Acpi.sys creates a filter device object, representing an ACPI bus filter, and attaches it to the device stack immediately above the bus driver (PDO). For other devices described in the ACPI namespace but not on the system board, Acpi.sys creates the PDO. Acpi.sys provides power management and PnP features to the device stack by means of these device objects. For more information, see [Device Stacks for an ACPI Device](https://docs.microsoft.com/windows-hardware/drivers/acpi/device-stacks-for-an-acpi-device).

A device for which Acpi.sys creates a device object is called an [ACPI device](https://docs.microsoft.com/windows-hardware/drivers/acpi/supporting-acpi-devices). The set of ACPI devices varies from one hardware platform to the next, and depends on the ACPI BIOS and the configuration of the motherboard. Note that Acpi.sys loads an ACPI bus filter only for a device that is described in the ACPI namespace and is permanently connected to the hardware platform (typically, this device is integrated into the core silicon or soldered to the system board). Not all motherboard devices have an ACPI bus filter.

All ACPI functionality is transparent to higher-level drivers. These drivers must make no assumptions about the presence or absence of an ACPI filter in any given device stack.

Acpi.sys and the ACPI BIOS support the basic functions of an ACPI device. To enhance the functionality of an ACPI device, the device vendor can supply a WDM function driver. For more information, see [Operation of an ACPI Device Function Driver](https://docs.microsoft.com/windows-hardware/drivers/acpi/operation-of-an-acpi-device-function-driver).

An ACPI device is specified by a definition block in the [system description tables](https://docs.microsoft.com/windows-hardware/drivers/bringup/acpi-system-description-tables) in the ACPI BIOS. A device's definition block specifies, among other things, an operation region, which is a contiguous block of device memory that is used to access device data. Only Acpi.sys modifies the data in an operation region. The device's function driver can read the data in an operation region but must not modify the data. When called, an [operation region handler](https://docs.microsoft.com/windows-hardware/drivers/acpi/implementing-an-operation-region-handler) transfers bytes in the operation region to and from the data buffer in Acpi.sys. The combined operation of the function driver and Acpi.sys is device-specific and is defined in the ACPI BIOS by the hardware vendor. In general, the function driver and Acpi.sys access particular areas in an operation region to perform device-specific operations and retrieve information. For more information, see [Supporting an Operation Region](https://docs.microsoft.com/windows-hardware/drivers/acpi/supporting-an-operation-region).

## ACPI control methods


ACPI control methods are software objects that declare and define simple operations to query and configure ACPI devices. Control methods are stored in the ACPI BIOS and are encoded in a byte-code format called ACPI Machine Language (AML). The control methods for a device are loaded from the system firmware into the device's ACPI namespace in memory, and interpreted by the Windows ACPI driver, Acpi.sys.

To invoke a control method, the kernel-mode driver for an ACPI device initiates an [**IRP\_MJ\_DEVICE\_CONTROL**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mj-device-control) request, which is handled by Acpi.sys. For drivers loaded on ACPI-enumerated devices, Acpi.sys always implements the physical device object (PDO) in the driver stack. For more information, see [Evaluating ACPI Control Methods](https://docs.microsoft.com/windows-hardware/drivers/acpi/evaluating-acpi-control-methods).

## ACPI specification


For the latest *Advanced Configuration and Power Interface Specification*, see the [ACPI 5.0 specification](https://uefi.org/specifications) available from the Unified Extensible Firmware Interface Forum website. 
Revision 5.0 of the ACPI specification introduces a set of features to support low-power, mobile PCs that are based on System on a Chip (SoC) integrated circuits and that implement the [connected standby](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby) power model. Starting with Windows 8 and Windows 8.1, the Windows ACPI driver, Acpi.sys, supports the new features in the ACPI 5.0 specification. For more information, see [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms).

## ACPI debugging


System integrators and ACPI device driver developers can use the Microsoft [AMLI debugger](https://docs.microsoft.com/windows-hardware/drivers/debugger/introduction-to-the-amli-debugger) to debug AML code. Because AML is an interpreted language, AML debugging requires special software tools.

For more information about the AMLI debugger, see [ACPI Debugging](https://docs.microsoft.com/windows-hardware/drivers/debugger/acpi-debugging).

For information about compiling ACPI Source Language (ASL) into AML, see [Microsoft ASL Compiler](https://docs.microsoft.com/windows-hardware/drivers/bringup/microsoft-asl-compiler).

 

 




