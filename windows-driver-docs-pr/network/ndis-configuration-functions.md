---
title: NDIS Configuration Functions
description: NDIS Configuration Functions
ms.assetid: 248e08d0-6145-499a-b307-2a5ffbd3733f
keywords:
- configuration functions WDK NDIS
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# NDIS Configuration Functions





NDIS includes the following functions to simplify driver configuration:

[**NdisOpenConfigurationEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisopenconfigurationex)

[**NdisMGetBusData**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismgetbusdata)

[**NdisMSetBusData**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismsetbusdata)

To obtain configuration information for an adapter, an NDIS miniport driver calls **NdisOpenConfigurationEx** and [**NdisReadConfiguration**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisreadconfiguration). The driver can call **NdisMGetBusData** to obtain bus-specific information. The driver can call **NdisMSetBusData** to set bus-specific information.

A protocol driver uses a registry path to an adapter name to read configuration parameters that are specific to the binding between the driver and the underlying adapter. NDIS provides the registry path in the call to the [*ProtocolBindAdapterEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-protocol_bind_adapter_ex) function. The driver can pass this registry path to the [**NdisOpenProtocolConfiguration**](https://docs.microsoft.com/previous-versions/windows/hardware/network/ff553683(v=vs.85)) function or to direct registry calls. As an alternative, the driver can pass a *BindParameters* structure to the **NdisOpenConfigurationEx** function to read the same parameters.

 

 





