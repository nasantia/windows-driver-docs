---
title: Querying Packet Coalescing Receive Filters
description: Querying Packet Coalescing Receive Filters
ms.assetid: D0B41718-37B9-4FB4-BA10-20765F836214
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Querying Packet Coalescing Receive Filters





Overlying drivers and applications can query packet coalescing receive filters that have been downloaded to a miniport driver by doing the following:

-   Request an enumerated list of the receive filters on the miniport driver by issuing an OID method request of [OID\_RECEIVE\_FILTER\_ENUM\_FILTERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-enum-filters). For more information, see [Enumerating the Receive Filters on a Miniport Driver](#enumerating-the-receive-filters-on-a-miniport-driver).

-   Request the test criterion parameters for a receive filter on the miniport driver by issuing an OID method request of [OID\_RECEIVE\_FILTER\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-parameters). For more information, see [Querying the Receive Filters on a Miniport Driver](#querying-the-parameters-of-a-receive-filters-on-a-miniport-driver)

NDIS handles the [OID\_RECEIVE\_FILTER\_ENUM\_FILTERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-enum-filters) and [OID\_RECEIVE\_FILTER\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-parameters) method OID requests for miniport drivers. NDIS obtained the information from an internal cache of the data that it received from the [OID\_RECEIVE\_FILTER\_SET\_FILTER](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-set-filter) OID request.

## Enumerating the Receive Filters on a Miniport Driver


To obtain a list of all the packet coalescing receive filters that have been downloaded to a miniport driver, overlying drivers and applications issue an OID method request of [OID\_RECEIVE\_FILTER\_ENUM\_FILTERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-enum-filters). The **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to an [**NDIS\_RECEIVE\_FILTER\_INFO\_ARRAY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_info_array) structure.

**Note**  When the overlying driver or application initializes the [**NDIS\_RECEIVE\_FILTER\_INFO\_ARRAY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_info_array) structure, it must set the **QueueId** member to NDIS\_DEFAULT\_RECEIVE\_QUEUE\_ID.

 

After a successful return from the OID method request, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to a buffer. This buffer is formatted to contain the following:

-   An [**NDIS\_RECEIVE\_FILTER\_INFO\_ARRAY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_info_array) structure that specifies a list of receive filters that are currently configured on a miniport driver.

-   An array of [**NDIS\_RECEIVE\_FILTER\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_info) structures about a receive filter that is currently configured on a miniport driver.

## Querying the Parameters of a Receive Filters on a Miniport Driver


To obtain the parameters of a specific packet coalescing receive filter that was downloaded to the miniport driver, overlying drivers or applications issue an OID method request of [OID\_RECEIVE\_FILTER\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-parameters). The **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to an [**NDIS\_RECEIVE\_FILTER\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_parameters) structure. The overlying driver or application initializes the **NDIS\_RECEIVE\_FILTER\_PARAMETERS** structure by setting the **FilterId** member to the nonzero ID value of the filter whose parameters are to be returned.

**Note**  The overlying driver obtained the filter ID from an earlier OID method request of [OID\_RECEIVE\_FILTER\_SET\_FILTER](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-set-filter) or [OID\_RECEIVE\_FILTER\_ENUM\_FILTERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-receive-filter-enum-filters). The application can only obtain the filter ID from an earlier OID method request of OID\_RECEIVE\_FILTER\_ENUM\_FILTERS.

 

After a successful return from the OID method request, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to a buffer. This buffer is formatted to contain the following:

-   An [**NDIS\_RECEIVE\_FILTER\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_parameters) structure that specifies the parameters for an NDIS receive filter.

-   An array of [**NDIS\_RECEIVE\_FILTER\_FIELD\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_receive_filter_field_parameters) structures that specifies the filter test criterion for one field in a network packet header.

 

 





