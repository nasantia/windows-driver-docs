---
title: NDIS_STATUS_WWAN_BASE_STATIONS_INFO
description: NDIS_STATUS_WWAN_BASE_STATIONS_INFO
ms.assetid: 57E22B53-5ECC-4B4C-8A98-C1125314868B
keywords:
- NDIS_STATUS_WWAN_BASE_STATIONS_INFO, base stations information query status notification, Mobile Broadband base stations information query status notification, MB base stations information query status notification
ms.date: 08/21/2017
ms.localizationpriority: medium
---

# NDIS_STATUS_WWAN_BASE_STATIONS_INFO

The NDIS_STATUS_WWAN_BASE_STATIONS_INFO notification is sent by modem miniport drivers in response to an [OID_WWAN_BASE_STATIONS_INFO](oid-wwan-base-stations-info.md) query request to provide the MB host with information about both serving and neighboring base stations.

This notification uses the [NDIS_WWAN_BASE_STATIONS_INFO](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_base_stations_info) structure.

## Requirements

| | |
| --- | --- |
| Version | Windows 10, version 1709 |
| Header | Ndis.h |

## See also

[OID_WWAN_BASE_STATIONS_INFO](oid-wwan-base-stations-info.md)

[NDIS_WWAN_BASE_STATIONS_INFO](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_base_stations_info)

[MB base stations information query operations](mb-base-stations-information-query-support.md)

