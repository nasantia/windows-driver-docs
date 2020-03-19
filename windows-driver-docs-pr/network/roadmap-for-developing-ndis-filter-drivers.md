---
title: Roadmap for Developing NDIS Filter Drivers
description: Roadmap for Developing NDIS Filter Drivers
ms.assetid: 346dae93-4cb7-4cb5-a2cf-41be9809fec2
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Roadmap for Developing NDIS Filter Drivers


To create a Network Driver Interface Specification (NDIS) filter driver package, follow these steps:

- Step 1: Learn about Windows architecture and drivers.

  You must understand the fundamentals of how drivers work in Windows operating systems. Knowing the fundamentals will help you make appropriate design decisions and let you streamline your development process. For more information about driver fundamentals, see [Concepts for all driver developers](https://docs.microsoft.com/windows-hardware/drivers/gettingstarted/concepts-and-knowledge-for-all-driver-developers).

- Step 2: Learn about NDIS.

  For general information about NDIS and NDIS drivers, see the following topics:

  [Windows Network Architecture and the OSI Model](windows-network-architecture-and-the-osi-model.md)

  [Network Driver Programming Considerations](network-driver-programming-considerations.md)

  [Driver Stack Management](driver-stack-management.md)

  [NET\_BUFFER Architecture](net-buffer-architecture.md)

- Step 3: Determine additional Windows driver design decisions.

  For more information about how to make additional Windows design decisions, see [Creating Reliable Kernel-Mode Drivers](https://docs.microsoft.com/windows-hardware/drivers/kernel/creating-reliable-kernel-mode-drivers), [Programming Issues for 64-Bit Drivers](https://docs.microsoft.com/windows-hardware/drivers/kernel/programming-issues-for-64-bit-drivers), and [Creating International INF Files](https://docs.microsoft.com/windows-hardware/drivers/install/creating-international-inf-files).

- Step 4: Learn about the Windows driver build, test, and debug processes and tools.

  Building a driver differs from building a user-mode application. For more information about Windows driver build, debug, and test processes, driver signing, and [Windows Hardware Compatibilty](https://docs.microsoft.com/windows-hardware/design/compatibility/) testing, see [Building, Debugging, and Testing Drivers](https://docs.microsoft.com/windows-hardware/drivers). For more information about building, testing, verifying, and debugging tools, see [Driver Development Tools](https://docs.microsoft.com/windows-hardware/drivers/devtest/index).

- Step 5: Read the [filter driver introduction topics](introduction-to-ndis-filter-drivers.md).

- Step 6: Read the [writing protocol drivers section](writing-ndis-miniport-drivers.md).

  This section provides an overview of the primary protocol driver interfaces. These interfaces included functions that protocol drivers provide (*ProtocolXxx* functions) and NDIS calls to initiate operations. NDIS provides **Ndis*Xxx*** functions that protocol drivers call to perform NDIS operations.

- Step 7: Review the [NDIS filter driver sample](https://go.microsoft.com/fwlink/p/?LinkId=617915) in the [Windows driver samples](https://go.microsoft.com/fwlink/p/?LinkId=616507) repository on GitHub..

- Step 8: Develop (or port), build, test, and debug your NDIS driver.

  See the porting guides if you are porting an existing driver:

  -   [Porting NDIS 5.x Drivers to NDIS 6.0](https://docs.microsoft.com/previous-versions/windows/hardware/network/porting-ndis-5-x-drivers-to-ndis-6-0)
  -   [Porting NDIS 6.x Drivers to NDIS 6.20](porting-ndis-6-x-drivers-to-ndis-6-20.md)
  -   [Porting NDIS 6.x Drivers to NDIS 6.30](porting-ndis-6-x-drivers-to-ndis-6-30.md)

  For more information about iterative building, testing, and debugging, see [Overview of Build, Debug, and Test Process](https://docs.microsoft.com/windows-hardware/drivers). This process will help ensure that you build a driver that works.

- Step 9: Create a driver package for your driver.

  For more information about how to install drivers, see [Providing a Driver Package](https://docs.microsoft.com/windows-hardware/drivers). For more information about how to install an NDIS driver, see [Installing and Upgrading Network Components](installing-and-upgrading-network-components.md).

- Step 10: Sign and distribute your driver.

  The final step is to sign (optional) and distribute the driver. If your driver meets the quality standards that are defined for the [Windows Hardware Compatibilty Program](https://docs.microsoft.com/windows-hardware/design/compatibility/), you can distribute it through the Microsoft Windows Update program. For more information about how to distribute a driver, see [Distributing a Driver](https://docs.microsoft.com/windows-hardware/drivers).

These are the basic steps. Additional steps might be necessary based on the needs of your individual driver.

 

 





