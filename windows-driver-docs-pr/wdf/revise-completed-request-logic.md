---
title: Revise Code That Handles Completed Requests
description: Revise Code That Handles Completed Requests
ms.assetid: 0DD48424-A728-4887-9F26-46B7004CB12C
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Revise Code That Handles Completed Requests


Windows Driver Frameworks (WDF) provides three methods that complete I/O requests:

-   [**WdfRequestComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcomplete)
-   [**WdfRequestCompleteWithInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithinformation)
-   [**WdfRequestCompleteWithPriorityBoost**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestcompletewithpriorityboost) (KMDF only)

For information about using these methods, see [Completing I/O Requests](completing-i-o-requests.md).

 

 





