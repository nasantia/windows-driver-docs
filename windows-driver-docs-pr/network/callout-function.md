---
title: Callout Function
description: Callout Function
ms.assetid: cf7b8e69-e6b2-41ac-9906-f0e3c090eb7a
keywords:
- callout functions WDK Windows Filtering Platform
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Callout Function


A *callout function* is a function that is implemented by a [callout driver](callout-driver.md) that is one of the functions that defines a [callout](callout.md). A callout consists of the following list of callout functions:

-   A [*notifyFn*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fwpsk/nc-fwpsk-fwps_callout_notify_fn0) function to process notifications.

-   A [*classifyFn*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fwpsk/nc-fwpsk-fwps_callout_classify_fn0) function to process classifications.

-   A [*flowDeleteFn*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fwpsk/nc-fwpsk-fwps_callout_flow_delete_notify_fn0) function to process flow deletions (optional).

The [filter engine](filter-engine.md) calls a callout's callout functions so that the callout can process the network data.

 

 





