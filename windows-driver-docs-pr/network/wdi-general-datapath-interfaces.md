---
title: WDI general datapath interfaces
description: This section describes general WDI datapath interfaces
ms.assetid: 5B40171C-4E5F-4C35-A6E7-1EA5181C02E8
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# WDI general datapath interfaces


## 802.11 frame handling and frame metadata


802.11 frames are passed between WDI and the TAL in the form of [**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) (NBL) chains. Each NBL represents one MSDU. Through macros, the NBL structure provides operations on the data buffers and access to metadata, including operating system populated Wi-Fi TX metadata. The structure is extensible through its context and **MiniportReserved** members. **MiniportReserved\[0\]** points to a buffer of type [**WDI\_FRAME\_METADATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dot11wdi/ns-dot11wdi-_wdi_frame_metadata). This buffer is allocated by WDI in the TX path, and by the TAL in the RX path via the callback [*NdisWdiAllocateWiFiFrameMetaData*](https://docs.microsoft.com/windows-hardware/drivers/ddi/dot11wdi/nc-dot11wdi-ndis_wdi_allocate_wdi_frame_metadata). The TAL uses MiniportReserved\[1\] to store any additional frame metadata.

## Datapath management requests and indications


For datapath management request and indication function reference, see [WDI Datapath Management Functions](https://docs.microsoft.com/windows-hardware/drivers/ddi/_netvista/).

## Related topics


[**NDIS\_WDI\_DATA\_API**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dot11wdi/ns-dot11wdi-_ndis_wdi_data_api)

[**NET\_BUFFER\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list)

[*NdisWdiAllocateWiFiFrameMetaData*](https://docs.microsoft.com/windows-hardware/drivers/ddi/dot11wdi/nc-dot11wdi-ndis_wdi_allocate_wdi_frame_metadata)

[**WDI\_FRAME\_METADATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dot11wdi/ns-dot11wdi-_wdi_frame_metadata)

 

 






