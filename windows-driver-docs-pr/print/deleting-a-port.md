---
title: Deleting a Port
description: Deleting a Port
ms.assetid: 0d491368-e529-4f04-a323-678e31a862c3
keywords:
- port management WDK print , deleting ports
- deleting print ports
- removing print ports
- DeletePort
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Deleting a Port





Deleting a port consists of removing the port's stored name and user-modifiable configuration information from the port monitor server DLL's local storage or from the registry.

When an application calls the print spooler's **DeletePort** function (described in the Microsoft Windows SDK documentation), the **DeletePort** function calls the [**DeletePortUI**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-deleteportui) function contained in the port monitor UI DLL of the appropriate port monitor.

The port monitor UI DLL's **DeletePortUI** function should perform the following operations:

1.  Call the print spooler's **OpenPrinter** function (described in the Windows SDK documentation), which causes the [**XcvOpenPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvopenport) function in the port monitor server DLL to be called.

2.  Call the print spooler's [**XcvData**](https://docs.microsoft.com/previous-versions/ff564255(v=vs.85)) function one or more times, to request the port monitor server DLL to delete the port. The **XcvData** function calls the server DLL's [**XcvDataPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvdataport) function.

3.  Call the print spooler's **ClosePrinter** function (described in the Windows SDK documentation), which causes the [**XcvClosePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvcloseport) function in the port monitor server DLL to be called.

For more information about these operations, see the description of [**DeletePortUI**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-deleteportui).

 

 




