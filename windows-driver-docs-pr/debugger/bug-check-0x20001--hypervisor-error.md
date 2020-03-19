---
title: Bug Check 0x20001 HYPERVISOR_ERROR
description: The HYPERVISOR_ERROR bug check has a value of 0x00020001. This indicates that the hypervisor has encountered a fatal error.
ms.assetid: 5F62DEEA-D192-46ED-827C-021A749D7091
keywords: ["Bug Check 0x20001 HYPERVISOR_ERROR", "HYPERVISOR_ERROR"]
ms.date: 04/12/2019
topic_type:
- apiref
api_name:
- HYPERVISOR_ERROR
api_type:
- NA
ms.localizationpriority: medium
---

# Bug Check 0x20001: HYPERVISOR\_ERROR


The HYPERVISOR\_ERROR bug check has a value of 0x00020001. This indicates that the hypervisor has encountered a fatal error.

> [!IMPORTANT]
> This topic is for programmers. If you are a customer who has received a blue screen error code while using your computer, see [Troubleshoot blue screen errors](https://www.windows.com/stopcode).

## HYPERVISOR\_ERROR Parameters


| Parameter | Description |
|-----------|-------------|
| 1         | Reserved    |
| 2         | Reserved    |
| 3         | Reserved    |
| 4         | Reserved    |

## Resolution 

The [**!analyze**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-analyze) debug extension displays information about the bug check and can be very in determining the root cause.