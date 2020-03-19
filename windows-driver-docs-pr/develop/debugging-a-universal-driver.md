---
title: Debugging a Universal Windows driver 
description: Describes debugging techniques you can use with a Universal Windows driver, in particular the Inflight Trace Recorder.
ms.date: 08/22/2019
ms.localizationpriority: medium
---

# Debugging a Universal Windows driver 

For general information about debugging universal drivers, see [Getting Started with Windows Debugging](https://docs.microsoft.com/windows-hardware/drivers/debugger/getting-started-with-windows-debugging).

## Inflight Trace Recorder

Starting in Windows 10, you can build your KMDF or UMDF driver binary so that it gets additional driver debugging information through the [Inflight Trace Recorder](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-wpp-recorder). Universal Windows drivers can take advantage of this feature.

In addition, if you used the Visual Studio KMDF template, your driver uses Windows software trace preprocessor (WPP) to write trace messages. Your driver binary is an ETW provider with a provider GUID.

To send a trace message from your driver binary, use this code:

   ```cpp
   TraceEvents(TRACE_LEVEL_INFORMATION, TRACE_DRIVER, "%!FUNC! Entry");
   ```

You can access the ETW logs using Tracelog by using [!wmitrace](https://docs.microsoft.com/windows-hardware/drivers/debugger/wmi-tracing-extensions--wmitrace-dll-) in a debugger session.

