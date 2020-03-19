---
title: Receiving Notifications
description: Receiving Notifications
ms.assetid: 852243b2-35b0-4c94-9b3b-9855ed1a678a
keywords:
- notifications WDK Native 802.11 IHV Extensions DLL
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Receiving Notifications




 

The operating system forwards IHV-specific indications from the Native 802.11 miniport driver by calling the [*Dot11ExtIhvReceiveIndication*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_indication) function. For more information about how the driver makes this type of indication, see [IHV-Specific Indications](ihv-specific-indications.md).

When the [*Dot11ExtIhvReceiveIndication*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_indication) function is called, the *pvBuffer* parameter is passed a pointer to a buffer that contains data in a format defined by the IHV.

 

 





