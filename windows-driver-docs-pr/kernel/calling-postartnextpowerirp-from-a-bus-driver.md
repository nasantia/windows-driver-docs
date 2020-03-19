---
title: Calling PoStartNextPowerIrp from a Bus Driver
description: Calling PoStartNextPowerIrp from a Bus Driver
ms.assetid: 4e23ebe1-c939-48e1-82bf-cdb4980a5a7b
keywords: ["bus drivers WDK power management", "power IRPs WDK kernel , PoStartNextPowerIrp", "PoStartNextPowerIrp"]
ms.date: 06/16/2017
ms.localizationpriority: medium
---

# Calling PoStartNextPowerIrp from a Bus Driver





Beginning with Windows Vista, calling [**PoStartNextPowerIrp**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-postartnextpowerirp) is not required and call to this routine performs no power management operation. However, in Windows Server 2003, Windows XP, and Windows 2000, a bus driver must call **PoStartNextPowerIrp** once for every [**IRP\_MN\_QUERY\_POWER**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-query-power) or [**IRP\_MN\_SET\_POWER**](https://docs.microsoft.com/windows-hardware/drivers/kernel/irp-mn-set-power) request that the driver receives.

A bus driver always calls this routine in its *DispatchPower* routine, before it calls the [**IoCompleteRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-iocompleterequest) routine.

 

 




