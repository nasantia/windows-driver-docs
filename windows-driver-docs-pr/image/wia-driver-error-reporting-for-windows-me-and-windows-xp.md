---
title: WIA Driver Error Reporting for Windows Me and Windows XP
description: WIA Driver Error Reporting for Windows Me and Windows XP
ms.assetid: 5f696e16-0c22-4d71-98d2-d642e721ac8c
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# WIA Driver Error Reporting for Windows Me and Windows XP

A WIA minidriver has the ability to report extended error information to the WIA application in string form. After receiving an HRESULT error code, a WIA application can call the **IWiaItemExtras::GetExtendedErrorInfo** method (described in the Microsoft Windows SDK documentation) for a user-readable string that describes the details of an error. The string reported by this method should be localized into multiple languages.

A WIA minidriver should implement the following methods to perform error reporting:

[**IStiUSD::GetLastError**](https://docs.microsoft.com/windows-hardware/drivers/ddi/stiusd/nf-stiusd-istiusd-getlasterror) − The WIA service calls this method to retrieve the device-specific error code for the recent failed action.

[**IStiUSD::GetLastErrorInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/stiusd/nf-stiusd-istiusd-getlasterrorinfo) − The WIA service calls this method to retrieve extended information about the error code returned from the **IStiUSD::GetLastError** method call.

[**IWiaMiniDrv::drvGetDeviceErrorStr**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvgetdeviceerrorstr) − The WIA service calls this method to retrieve any displayable strings that describe the error in detail, or instructions to the end user on how to proceed after the error. The **IWiaItemExtras::GetExtendedErrorInfo** method returns the error string this method retrieved.

The WIA service asks for error information if any of the [IWiaMiniDrv COM Interface](iwiaminidrv-com-interface.md) methods fail.
