---
title: GUID_NDIS_STATUS_OPER_STATUS
description: This topic describes the GUID_NDIS_STATUS_OPER_STATUS GUID for the NDIS WMI interface.
ms.assetid: e4e13f9d-6298-47b0-9cb1-70fea87db59a
keywords:
- GUID_NDIS_STATUS_OPER_STATUS, WDK GUID_NDIS_STATUS_OPER_STATUS network drivers
ms.date: 11/22/2017
ms.localizationpriority: medium
---

# GUID_NDIS_STATUS_OPER_STATUS

The GUID_NDIS_STATUS_OPER_STATUS event GUID indicates the current operational state of an NDIS network interface. This WMI GUID is supported in NDIS 6.0 and later versions.

NDIS generates an [NDIS_STATUS_OPER_STATUS](ndis-status-oper-status.md) status indication to report the current operational state of an NDIS network interface.

When NDIS indicates a change in the current operational state of an NDIS network interface, NDIS also translates the status indication to a WMI GUID_NDIS_STATUS_OPER_STATUS event for WMI clients.

The data buffer that NDIS provides with the GUID contains an [NDIS_WMI_EVENT_HEADER](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_wmi_event_header) structure that is followed by an [NDIS_OPER_STATE](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_oper_state) structure. For a list of the possible values, see [NDIS_STATUS_OPER_STATUS](ndis-status-oper-status.md).

