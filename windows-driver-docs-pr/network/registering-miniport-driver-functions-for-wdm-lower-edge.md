---
title: Registering Miniport Driver Functions for WDM Lower Edge
description: Registering Miniport Driver Functions for WDM Lower Edge
ms.assetid: 68048d36-d57c-4ad9-a15e-92b1d7866d4a
keywords:
- NDIS-WDM miniport drivers WDK networking , registering functions
- NDIS-WDM miniport drivers WDK networking , entry-point functions
- lower edge of NDIS miniport drivers WDK networking , entry-point functions
- WDM lower edge WDK networking , entry-point functions
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Registering Miniport Driver Functions for WDM Lower Edge





A miniport driver that has a WDM lower edge must call the [**NdisMRegisterMiniportDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismregisterminiportdriver) function in its **DriverEntry** routine to register certain entry-point functions with the NDIS library. These entry-point functions compose the miniport driver's upper edge and are described in [Initializing a Miniport Driver](initializing-a-miniport-driver.md). However, a miniport driver that has a WDM lower edge is not required to set up certain entry-point functions. For example, the following entry-point functions are not set up for the following reasons:

-   [*MiniportInterrupt*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_isr), [*MiniportInterruptDPC*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_interrupt_dpc), [*MiniportEnableInterruptEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_enable_interrupt), and [*MiniportDisableInterruptEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_disable_interrupt)

    Because the miniport driver does not receive interrupts from a physical network interface card (NIC), it does not require these entry-point routines. The driver for the particular bus receives interrupts when packets arrive on the bus that are intended for the miniport driver. The bus driver then notifies the miniport driver.

-   [*MiniportSharedMemoryAllocateComplete*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_allocate_shared_mem_complete)

    Because the miniport driver does not allocate shared memory, a completion entry-point routine is not specified.

-   [*MiniportCheckForHangEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_check_for_hang)

    The miniport driver can rely on NDIS to determine if its miniport instance has stopped responding, based on sends and requests that time out, so this routine is not typically required.

 

 





