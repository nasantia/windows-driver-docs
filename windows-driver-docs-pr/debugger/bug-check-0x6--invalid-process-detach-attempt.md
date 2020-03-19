---
title: Bug Check 0x6 INVALID_PROCESS_DETACH_ATTEMPT
description: The INVALID_PROCESS_DETACH_ATTEMPT bug check has a value of 0x00000006. This bug check appears very infrequently.
ms.assetid: f468b348-6576-4430-aa8f-b6100a689fee
keywords: ["Bug Check 0x6 INVALID_PROCESS_DETACH_ATTEMPT", "INVALID_PROCESS_DETACH_ATTEMPT"]
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- INVALID_PROCESS_DETACH_ATTEMPT
api_type:
- NA
ms.localizationpriority: medium
---

# Bug Check 0x6: INVALID\_PROCESS\_DETACH\_ATTEMPT


The INVALID\_PROCESS\_DETACH\_ATTEMPT bug check has a value of 0x00000006.

This bug check appears very infrequently. This bug check can be caused by calling the [**KeStackAttachProcess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-kestackattachprocess) routine and subsequently calling [**KeUnstackDetachProcess**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/nf-ntifs-keunstackdetachprocess) in the driver's implementation of the [**PLOAD_IMAGE_NOTIFY_ROUTINE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nc-ntddk-pload_image_notify_routine) callback function. The callback runs in a thread of the process in which the image loaded.

> [!IMPORTANT]
> This topic is for programmers. If you are a customer who has received a blue screen error code while using your computer, see [Troubleshoot blue screen errors](https://www.windows.com/stopcode).


 

 




