---
title: Bug Check 0xDC DRIVER_INVALID_STACK_ACCESS
description: The DRIVER_INVALID_STACK_ACCESS bug check has a value of 0x000000DC. This indicates that a driver accessed a stack address that lies below the stack pointer of the stack's thread.
ms.assetid: efc2201f-b2e5-458b-a2b0-26abaa46f1a4
keywords: ["Bug Check 0xDC DRIVER_INVALID_STACK_ACCESS", "DRIVER_INVALID_STACK_ACCESS"]
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- DRIVER_INVALID_STACK_ACCESS
api_type:
- NA
ms.localizationpriority: medium
---

# Bug Check 0xDC: DRIVER\_INVALID\_STACK\_ACCESS


The DRIVER\_INVALID\_STACK\_ACCESS bug check has a value of 0x000000DC. This indicates that a driver accessed a stack address that lies below the stack pointer of the stack's thread.

> [!IMPORTANT]
> This topic is for programmers. If you are a customer who has received a blue screen error code while using your computer, see [Troubleshoot blue screen errors](https://www.windows.com/stopcode).


## DRIVER\_INVALID\_STACK\_ACCESS Parameters


None

 
## Remarks
The [**!analyze**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-analyze) debug extension displays information about the bug check and can be helpful in determining the root cause.
 




