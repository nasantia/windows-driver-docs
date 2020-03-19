---
title: NDIS_STATUS_WWAN_MODEM_LOGGING_CONFIG
description: Miniport drivers use the NDIS_STATUS_WWAN_MODEM_LOGGING_CONFIG notification to inform the mobile broadband (MB) service about the completion of a previous OID_WWAN_MODEM_LOGGING_CONFIG Query or Set request.
ms.assetid: 0370C672-B7A7-4ECE-94F6-FC04407959E4
ms.date: 04/11/2019
keywords: 
 -NDIS_STATUS_WWAN_MODEM_LOGGING_CONFIG Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
ms.custom: 19H1
---

# NDIS_STATUS_WWAN_MODEM_LOGGING_CONFIG

Miniport drivers use the **NDIS_STATUS_WWAN_MODEM_LOGGING_CONFIG** notification to inform the mobile broadband (MB) service about the completion of a previous [OID_WWAN_MODEM_LOGGING_CONFIG](oid-wwan-modem-logging-config.md) Query or Set request.

Miniport drivers send this notification as an unsolicited event in scenarios where the modem needs to inform the OS about internal changes. Currently, in Windows 10, version 1903, these scenarios do not occur.

This notification uses the [**NDIS_WWAN_MODEM_LOGGING_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_modem_logging_config) structure.

## Requirements

|   |   |
| --- | --- |
| Version | Windows 10, version 1903 |
| Header | Ntddndis.h (include Ndis.h) |

## See also

[MB modem logging with DSS](mb-modem-logging-with-dss.md)

[OID_WWAN_MODEM_LOGGING_CONFIG](oid-wwan-modem-logging-config.md)

[**NDIS_WWAN_MODEM_LOGGING_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_modem_logging_config)
