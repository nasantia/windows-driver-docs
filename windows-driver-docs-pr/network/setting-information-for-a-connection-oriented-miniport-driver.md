---
title: Setting Information for a Connection-Oriented Miniport Driver
description: Setting Information for a Connection-Oriented Miniport Driver
ms.assetid: e31d2054-5982-4ba5-a9e9-133c0d4ed875
keywords:
- connection-oriented drivers WDK networking
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Setting Information for a Connection-Oriented Miniport Driver





To set an OID that a connection-oriented miniport driver maintains, a bound protocol calls [**NdisCoOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscooidrequest) and passes an [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure that specifies the object (OID) that is being queried and that points to a buffer that contains the value to which the object should be set. The call to **NdisCoOidRequest** causes NDIS to call the miniport driver's [**MiniportCoOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_co_oid_request) function, which sets the object with the supplied value.

The call to **NdisCoOidRequest** can complete synchronously or asynchronously. To complete the call asynchronously, a miniport driver calls [**NdisCoOidRequestComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscooidrequestcomplete). The following diagram illustrates setting information in a connection-oriented miniport driver.

![diagram illustrating setting information in a connection-oriented miniport driver](images/fig5-3.png)

 

 





