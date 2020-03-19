---
title: Querying NDIS QoS Parameters
description: Querying NDIS QoS Parameters
ms.assetid: 875D39BA-D70D-4450-9F64-D08EAB54BDC2
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Querying NDIS QoS Parameters


Overlying protocol and filter drivers can query the NDIS Quality of Service (QoS) parameters of a network adapter in the following ways:

-   The overlying driver can query the operational NDIS QoS parameters through an object identifier (OID) query request of [OID\_QOS\_OPERATIONAL\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-qos-operational-parameters).

-   The overlying driver can query the remote NDIS QoS parameters through an OID query request of [OID\_QOS\_REMOTE\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-qos-remote-parameters).

**Note**  Overlying drivers cannot query the local NDIS QoS parameters.

 

For more information about local, remote, and operational NDIS QoS parameters, see [Overview of NDIS QoS Parameters](overview-of-ndis-qos-parameters.md).

NDIS handles these OID requests for the miniport driver and returns the requested QoS parameters within an [**NDIS\_QOS\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_qos_parameters) structure. NDIS handles these OID requests in the following ways:

-   When NDIS handles the OID query request of [OID\_QOS\_OPERATIONAL\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-qos-operational-parameters), it returns the operational NDIS QoS parameters that it had cached from the previous [**NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-operational-parameters-change) status indication that was issued by the miniport driver. The driver issues this status indication when its operational QoS parameters are either resolved for the first time or change later.

    If the overlying driver issues the OID query request before the miniport driver issues the [**NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-operational-parameters-change) status indication, NDIS returns an [**NDIS\_QOS\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_qos_parameters) structure with all the members (with the exception of the **Header** member) set to zero.

    **Note**  NDIS also returns this structure if the miniport driver issues an [**NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-operational-parameters-change) status indication with an [**NDIS\_QOS\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_qos_parameters) structure whose members (with the exception of the **Header** member) are set to zero.

     

-   When NDIS handles the OID query request of [OID\_QOS\_REMOTE\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-qos-remote-parameters), it returns the remote NDIS QoS parameters that it had cached from the previous [**NDIS\_STATUS\_QOS\_REMOTE\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-remote-parameters-change) status indication that was issued by the miniport driver. The driver issues this status indication when its remote QoS parameters are either resolved for the first time or change later.

    If the overlying driver issues the OID query request before the miniport driver issues the [**NDIS\_STATUS\_QOS\_REMOTE\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-remote-parameters-change) status indication, NDIS returns an [**NDIS\_QOS\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_qos_parameters) structure with all the members (with the exception of the **Header** member) set to zero.

    **Note**  NDIS also returns this structure if the miniport driver issues an [**NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE**](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-status-qos-operational-parameters-change) status indication with an [**NDIS\_QOS\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_qos_parameters) structure whose members (with the exception of the **Header** member) are set to zero.

     

 

 





