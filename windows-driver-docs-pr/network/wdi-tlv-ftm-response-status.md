---
title: WDI_TLV_FTM_RESPONSE_STATUS
description: WDI_TLV_FTM_RESPONSE_STATUS is a TLV that contains the Fine Timing Measurement (FTM) response status from a target BSS.
ms.assetid: 49C3759C-3F3F-4C2D-863E-28227ED323BA
ms.date: 02/15/2019
keywords:
 - WDI_TLV_FTM_RESPONSE_STATUS Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
ms.custom: 19H1
---

# WDI_TLV_FTM_RESPONSE_STATUS

**WDI_TLV_FTM_RESPONSE_STATUS** is a TLV that contains the Fine Timing Measurement (FTM) response status from a target BSS.

This TLV is used in [WDI_TLV_FTM_RESPONSE](wdi-tlv-ftm-response.md).

## TLV Type

0x159

## Length

The size (in bytes) of a UINT32.

## Values

| Type | Description |
| --- | --- |
| [**WDI_FTM_RESPONSE_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wditypes/ne-wditypes-_wdi_ftm_response_status) | The FTM response status. |

## Requirements

|   |   |
| --- | --- |
| Minimum supported client | Windows 10, version 1903 |
| Minimum supported server | Windows Server 2016 |
| Header | Wditypes.hpp |
