---
title: Setting Value Data by Specifying Its Usage
description: Setting Value Data by Specifying Its Usage
ms.assetid: 69dc3bb4-8999-4990-950c-8581328030eb
keywords: ["HID reports WDK , setting control data", "reports WDK HID , setting control data", "data usage settings WDK HID"]
ms.localizationpriority: medium
ms.date: 10/17/2018
---

# Setting Value Data by Specifying Its Usage





An application or driver can set a value in a properly-initialized HID report by calling one of the following HID support routines:

<a href="" id="hidp-setscaledusagevalue"></a>[**HidP\_SetScaledUsageValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/hidpi/nf-hidpi-hidp_setscaledusagevalue)  
Sets a signed and scaled value in a report.

<a href="" id="hidp-setusagevalue"></a>[**HidP\_SetUsageValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/hidpi/nf-hidpi-hidp_setusagevalue)  
Sets a value in a report.

<a href="" id="hidp-setusagevaluearray"></a>[**HidP\_SetUsageValueArray**](https://docs.microsoft.com/windows-hardware/drivers/ddi/hidpi/nf-hidpi-hidp_setusagevaluearray)  
Sets a usage value array in a report.

<a href="" id="see-also-initializing-hid-reports-"></a>See also [Initializing HID Reports](initializing-hid-reports.md).  

 

 




