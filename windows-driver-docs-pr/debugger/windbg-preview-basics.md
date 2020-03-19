---
title: WinDbg Preview Basics 
description: This section describes the basic capabilities of WinDbg preview debugger.
ms.date: 05/02/2019
ms.localizationpriority: medium
---

# WinDbg Preview Basics

![Small logo on windbg preview](images/windbgx-preview-logo.png) 

| Title               | Description        |
| ------------------- | -------------------|
|[WinDbg Preview - What's New](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugging-using-windbg-preview)|What's new with WinDbg Preview |

## The debugger data model

| Title               | Description        |
| ------------------- | -------------------|
| [dx command](https://docs.microsoft.com/windows-hardware/drivers/debugger/dx--display-visualizer-variables-) | Interactive command to display a debugger object model expression |
| [Using LINQ With the debugger objects](https://docs.microsoft.com/windows-hardware/drivers/debugger/using-linq-with-the-debugger-objects) | SQL like query language |
| [Native Debugger Objects in NatVis](https://docs.microsoft.com/windows-hardware/drivers/debugger/native-debugger-objects-in-natvis)| Using the objects with NatVis |
| [WinDbg Preview - Data model](windbg-data-model-preview.md) | How to use the built in data model support in WinDbg Preview |

## Extending the data model

| Title               | Description        |
| ------------------- | -------------------|
| [JavaScript Debugger Scripting](https://docs.microsoft.com/windows-hardware/drivers/debugger/javascript-debugger-scripting) | How to use JavaScript to create scripts that understand debugger objects  |
| [WinDbg Preview - Scripting](https://docs.microsoft.com/windows-hardware/drivers/debugger/windbg-scripting-preview) |Using the WinDbg Preview built in scripting  |
| https://github.com/Microsoft/WinDbg-Samples |The debugger team GitHub site where they share the latest JavaScript (and C++) sample code. |
|[Native Debugger Objects in JavaScript Extensions](https://docs.microsoft.com/windows-hardware/drivers/debugger/native-objects-in-javascript-extensions) | Describes how to work with common objects and provides reference information on their attributes and behaviors.|

## TTD Basics

| Title               | Description        |
| ------------------- | -------------------|
| [Time Travel Debugging - Overview](https://docs.microsoft.com/windows-hardware/drivers/debugger/time-travel-debugging-overview) | TTD Overview |
[Time Travel Debugging - Sample App Walkthrough](https://docs.microsoft.com/windows-hardware/drivers/debugger/time-travel-debugging-walkthrough) |  To give time travel a try checkout this tutorial |

## TTD queries
| Title               | Description        |
| ------------------- | -------------------|
| [Introduction to Time Travel Debugging objects](https://docs.microsoft.com/windows-hardware/drivers/debugger/time-travel-debugging-object-model). |You can use the data model to query time travel traces.  
|  https://github.com/Microsoft/WinDbg-Samples/blob/master/TTDQueries/tutorial-instructions.md |A tutorial on how to debug C++ code using TTD queries to find the problematic code |
| https://github.com/Microsoft/WinDbg-Samples/tree/master/TTDQueries/app-sample | All of the code used in the lab is available here.

## Videos

Watch these episodes of [Defrag Tools](https://channel9.msdn.com/Shows/Defrag-Tools) to see Windbg Preview in action.  

| Title               | Description        |
|-------------------- |--------------------|
| [Defrag Tools #182](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-182-WinDbg-Preview-Part-1) |Tim, Chad, and Andy go over the basics of WinDbg Preview and some of the features |
| [Defrag Tools #183](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-183-WinDbg-Preview-Part-2) | Nick, Tim, and Chad use WinDbg Preview and go over a quick demo |
| [Defrag Tools #184](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-184-JavaScript-in-WinDbg-Preview) | Bill and Andrew walk through the scripting features in WinDbg Preview |
| [Defrag Tools #185](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-185-Time-Travel-Debugging-Introduction) | James and Ivette provide and introduction to Time Travel Debugging |
| [Defrag Tools #186](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-186-Time-Travel-Debugging-Advanced) | James and JCAB covers advanced Time Travel Debugging |

## Installation and getting connected 

| Title               | Description        |
| ------------------- | -------------------|
| [WinDbg Preview – Installation](windbg-install-preview.md) | Installation directions |
| [WinDbg Preview – Start a user-mode session](windbg-user-mode-preview.md) | User Mode  |
| [WinDbg Preview – Start a kernel mode session](windbg-kernel-mode-preview.md) | Kernel Mode |
