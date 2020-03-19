---
title: Synchronizing with Interrupts
description: Synchronizing with Interrupts
ms.assetid: f201acfa-98e4-4373-ba63-b6c814810f99
keywords:
- interrupts WDK networking , synchronizing
- NdisMSynchronizeWithInterruptEx
- synchronization WDK interrupts
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Synchronizing with Interrupts





If a miniport driver's [*MiniportInterrupt*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_isr) function shares resources, such as NIC registers or state variables, with another *MiniportXxx* function that runs at a lower IRQL, that *MiniportXxx* function must call [**NdisMSynchronizeWithInterruptEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsynchronizewithinterruptex). This call ensures that the miniport driver's [*MiniportSynchronizeInterrupt*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_synchronize_interrupt) function accesses the shared resources in a synchronized and multiprocessor-safe manner.

 

 





