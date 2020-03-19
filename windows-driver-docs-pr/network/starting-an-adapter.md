---
title: Starting an Adapter
description: Starting an Adapter
ms.assetid: ff2c8914-2fc2-4182-b47e-685571508b33
keywords:
- miniport adapters WDK networking , starting
- adapters WDK networking , starting
- Paused state WDK networking
- Running state WDK networking
- MiniportRestart
- starting miniport adapters
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Starting an Adapter





NDIS calls a miniport driver's [**MiniportRestart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_restart) function to initiate a restart request for an adapter that is in the Paused state. The driver can resume indicating received data immediately after NDIS calls *MiniportRestart* and before the miniport driver completes the restart operation, either synchronously or asynchronously.

When it calls a miniport driver's [**MiniportRestart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_restart) function, NDIS passes a pointer to an [**NDIS\_RESTART\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_restart_attributes) structure to the miniport driver in the **RestartAttributes** member of the [**NDIS\_MINIPORT\_RESTART\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_miniport_restart_parameters) structure.

To complete the restart operation asynchronously, *MiniportRestart* returns NDIS\_STATUS\_PENDING and the driver must call the [**NdisMRestartComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismrestartcomplete) function after the operation is complete.

The miniport driver should be ready to accept send requests after it completes the restart operation. NDIS does not initiate any other Plug and Play operations, such as halt, initialize, or a pause request, until the restart operation is complete.

After the driver is ready to handle send and receive operations, the adapter is in the Running state.

 

 





