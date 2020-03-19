---
title: Network Interface Information
description: Network Interface Information
ms.assetid: 4d8cd9c2-6f78-4c70-83bd-f36fffbf1c35
keywords:
- NDIS network interfaces WDK , information about
- network interfaces WDK , information about
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Network Interface Information





An interface provider supplies information about each registered interface by using the following data structures.

-   [**NET\_IF\_INFORMATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_if_information)

-   [**NDIS\_INTERFACE\_INFORMATION**](https://docs.microsoft.com/windows/desktop/api/ifdef/ns-ifdef-_ndis_interface_information)

To register an interface, a provider passes a pointer to an initialized NET\_IF\_INFORMATION structure to the [**NdisIfRegisterInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisifregisterinterface) function.

NDIS interface providers provide an [**NDIS\_INTERFACE\_INFORMATION**](https://docs.microsoft.com/windows/desktop/api/ifdef/ns-ifdef-_ndis_interface_information) structure in response to a query of the [OID\_GEN\_INTERFACE\_INFO](https://docs.microsoft.com/windows-hardware/drivers/network/oid-gen-interface-info) OID.

NDIS can also query providers with other OIDs. For more information about NDIS provider OIDs, see [NDIS Network Interface to OID Mapping](mapping-of-ndis-network-interfaces-to-ndis-oids.md). For more information about handling OID requests in interface providers, see [Handling OID Query and Set Requests in an NDIS Interface Provider](handling-oid-query-and-set-requests-in-an-ndis-interface-provider.md).

 

 





