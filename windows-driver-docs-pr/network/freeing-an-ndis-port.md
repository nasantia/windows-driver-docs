---
title: Freeing an NDIS Port
description: Freeing an NDIS Port
ms.assetid: ae7b608d-6105-4fdc-b805-0f0101d7c218
keywords:
- ports WDK NDIS , freeing
- NDIS ports WDK , freeing
- freeing NDIS ports
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Freeing an NDIS Port





Your miniport driver must free all NDIS ports that it [allocates](allocating-an-ndis-port.md) for miniport adapters in its [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) function. It can free a port any time by calling [**NdisMFreePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismfreeport), except for the two cases noted below.

Your miniport driver must free all allocated ports in these cases:

-   If your driver’s [*MiniportInitializeEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_initialize) function fails, it must free all allocated ports.
-   If a miniport adapter is halted, your driver’s [*MiniportHaltEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_halt) function must free all allocated ports.

Your miniport driver cannot simply call [**NdisMFreePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismfreeport) in these cases:

-   If the port is the default port, NDIS frees it automatically, so your miniport driver must not free it. If you try to free the [default port](default-ndis-port.md), [**NdisMFreePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismfreeport) returns an NDIS\_STATUS\_INVALID\_PORT error.
-   If the port is active, your miniport driver will need to deactivate it before calling [**NdisMFreePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismfreeport).

## Related topics


[Allocating NDIS Ports](allocating-an-ndis-port.md)

[Deactivating NDIS Ports](deactivating-an-ndis-port.md)

[Default NDIS Port](default-ndis-port.md)

 

 






