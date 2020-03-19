---
title: Printing a Print Job
description: Printing a Print Job
ms.assetid: 2e881f99-9dbe-4e89-8628-feb05137c9b0
keywords:
- print monitors WDK , printing print jobs
- print jobs WDK , printing
- jobs WDK print , printing
- WritePort
- ReadPort
- GetPrinterDataFromPort
- bidirectional communication WDK print
- bidi communication WDK print
- printing print jobs WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Printing a Print Job





After a port has been opened, as described in [Opening and Closing a Port](opening-and-closing-a-port.md), the spooler can send print jobs to the port.

Each print job is delimited by spooler calls to a language or port monitor's [**StartDocPort**](https://docs.microsoft.com/previous-versions/ff562710(v=vs.85)) and [**EndDocPort**](https://docs.microsoft.com/previous-versions/ff548742(v=vs.85)) functions. The spooler calls these functions when a print processor calls the spooler's **StartDocPrinter** and **EndDocPrinter** functions, which are described in the Microsoft Windows SDK documentation. Within the scope of a set of **StartDocPort** and **EndDocPort** functions, unlimited spooler calls to a monitor's [**WritePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-writeport), [**ReadPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-readport), and [**GetPrinterDataFromPort**](https://docs.microsoft.com/previous-versions/ff550506(v=vs.85)) functions can occur.

Each of these functions requires the port handle returned by [**OpenPortEx**](https://docs.microsoft.com/previous-versions/ff559596(v=vs.85)) (or [**OpenPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-openport)) to be specified as in input argument. Typically, a language monitor implements each of the functions by calling the like-named function in its associated port monitor.

When the spooler calls a language monitor's **WritePort** function to send a data stream to the port, the function generally adds language-specific information, such as *PJL* commands, to the received data stream before passing it to the associated port monitor's **WritePort** function.

The **ReadPort** function is used for obtaining status information from bidirectional printer hardware, which a language monitor might send to the spooler by calling **SetPort**, described in the Windows SDK documentation. The spooler does not call the **ReadPort** function.

If printing hardware is bidirectional, both its language monitor and its port monitor should support a **GetPrinterDataFromPort** function. A language monitor's **GetPrinterDataFromPort** function should accept a registry value name as input, obtain a value for that name (generally by calling associated port monitor's **WritePort** and **ReadPort** functions), and return the value to the caller. A port monitor's **GetPrinterDataFromPort** function should accept an I/O control code as input, call [**DeviceIoControl**](https://docs.microsoft.com/windows/desktop/api/ioapiset/nf-ioapiset-deviceiocontrol) (described in the Windows SDK documentation) to pass the control code to the port driver, and return the result.

 

 




