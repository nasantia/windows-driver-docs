---
title: Note to discourage NDIS DMA use on ARM/ARM64 processors
ms.localizationpriority: medium
ms.date: 10/17/2018
---

# Note to discourage NDIS DMA use on ARM/ARM64 processors

> [!CAUTION]
> For ARM and ARM64 processors, we strongly recommend that NDIS driver writers use WDF DMA or WDM DMA instead of NDIS Scatter/Gather DMA.
>
> For more information about WDF DMA, see [Handling DMA Operations in KMDF Drivers](../wdf/handling-dma-operations-in-kmdf-drivers.md).
>
> For more information about WDM DMA, see the DMA-related child topics of [Managing Input/Output for Drivers](../kernel/managing-input-output-for-drivers.md).
