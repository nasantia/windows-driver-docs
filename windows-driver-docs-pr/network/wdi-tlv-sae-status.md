---
title: WDI_TLV_SAE_STATUS
description: WDI_TLV_SAE_STATUS is a TLV that contains Simultaneous Authentication of Equals (SAE) authentication failure error status.
ms.assetid: 7B6B8D4B-35B4-4AEA-A969-4BB514AB968E
ms.date: 02/15/2019
keywords:
 - WDI_TLV_SAE_STATUS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
ms.custom: 19H1
---

# WDI_TLV_SAE_STATUS

**WDI_TLV_SAE_STATUS** is a TLV that contains Simultaneous Authentication of Equals (SAE) authentication failure error status.

This TLV is used in the command parameters of [OID_WDI_SET_SAE_AUTH_PARAMS](oid-wdi-set-sae-auth-params.md) and in the payload data of [NDIS_STATUS_WDI_INDICATION_SAE_AUTH_PARAMS_NEEDED](ndis-status-wdi-indication-sae-auth-params-needed.md).

## TLV Type

0x14C

## Length

The size (in bytes) of a UINT32.

## Values

| Type | Description |
| --- | --- |
| [**WDI_SAE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wditypes/ne-wditypes-_wdi_sae_status) | The SAE authentication failure error status. |

## Requirements

|   |   |
| --- | --- |
| Minimum supported client | Windows 10, version 1903 |
| Minimum supported server | Windows Server 2016 |
| Header | Wditypes.hpp |
