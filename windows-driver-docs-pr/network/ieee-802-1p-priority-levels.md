---
title: IEEE 802.1p Priority Levels
description: IEEE 802.1p Priority Levels
ms.assetid: C7EB3D85-544E-4898-A456-843621F6488D
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# IEEE 802.1p Priority Levels


IEEE 802.1p was specified by an IEEE 802.1 Task Group to address traffic prioritization for Quality of Service (QoS). 802.1p is not a separate IEEE 802.1 standard, but is defined in Annex G of the IEEE 802.1Q-2005 standard.

IEEE 802.1p defines a 3-bit field called the Priority Code Point (PCP) within an IEEE 802.1Q tag. For NDIS packets, the 802.1p PCP value is specified by the **UserPriority** member of the [**NDIS\_NET\_BUFFER\_LIST\_8021Q\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_net_buffer_list_8021q_info) structure that is associated with a packet's [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) structure.

The PCP value defines 8 priority levels, with 7 the highest priority and 1 the lowest priority. The priority level of 0 is the default. Each priority level defines a *class of service* that identifies separate traffic classes of transmitted packets.

 

 





