---
title: Summary of Debugger Extensions in Wdfkd.dll
description: The Windows Driver Kit (WDK) includes a debugger extension library, named Wdfkd.dll.
ms.assetid: 5a83ea58-5dbf-40a6-b4cb-9c330851fc33
keywords:
- extensions WDK debuggers
- debugger extensions WDK KMDF
- debugging drivers WDK KMDF , debugger extensions
ms.date: 04/20/2017
ms.localizationpriority: medium
---

#  Summary of Debugger Extensions in Wdfkd.dll


The Windows Driver Kit (WDK) includes a debugger extension library, named *Wdfkd.dll*. This library contains debugger extension commands that you can use to debug both Kernel-Mode Driver Framework (KMDF) and User-Mode Driver Framework (UMDF) drivers starting with version 2.

For a complete description of each command, see [**Windows Driver Framework Extensions (Wdfkd.dll)**](https://docs.microsoft.com/windows-hardware/drivers/debugger/kernel-mode-driver-framework-extensions--wdfkd-dll-). For more information about all available debugger extension libraries, see the documentation that is supplied with the [Windows Debugging](https://docs.microsoft.com/windows-hardware/drivers/debugger/index) package.

You can find a video series that demonstrates how to debug a KMDF driver at [Videos: Debugging KMDF Drivers](debugging-kernel-mode-driver-framework-drivers.md).

To debug a driver that uses UMDF version 1.11 or earlier, you must instead use the *Wudfext.dll* debugger extension library. For more info, see [User-Mode Driver Framework Extensions (Wudfext.dll)](https://docs.microsoft.com/windows-hardware/drivers/debugger/user-mode-driver-framework-extensions--wudfext-dll-).

The extension commands that the *Wdfkd.dll* extension library provides include:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Extension</th>
<th align="left">Description</th>
<th align="left">Frameworks</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfhelp" data-raw-source="[&lt;strong&gt;!wdfkd.wdfhelp&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfhelp)"><strong>!wdfkd.wdfhelp</strong></a></p></td>
<td align="left"><p>Displays this list of debugger extensions.</p></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfchildlist" data-raw-source="[&lt;strong&gt;!wdfkd.wdfchildlist&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfchildlist)"><strong>!wdfkd.wdfchildlist</strong></a></p></td>
<td align="left"><p>Displays a child list's state and information about all of the device identification descriptions that are in the child list.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcollection" data-raw-source="[&lt;strong&gt;!wdfkd.wdfcollection&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcollection)"><strong>!wdfkd.wdfcollection</strong></a></p></td>
<td align="left"><p>Displays the objects that are contained in a collection.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcommonbuffer" data-raw-source="[&lt;strong&gt;!wdfkd.wdfcommonbuffer&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcommonbuffer)"><strong>!wdfkd.wdfcommonbuffer</strong></a></p></td>
<td align="left"><p>Displays information about a <a href="using-common-buffers.md" data-raw-source="[common buffer object](using-common-buffers.md)">common buffer object</a>.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcrashdump" data-raw-source="[&lt;strong&gt;!wdfkd.wdfcrashdump&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfcrashdump)"><strong>!wdfkd.wdfcrashdump</strong></a></p></td>
<td align="left"><p>Displays the framework's event log records, if available, from a small memory dump. The framework's event log records are available if <a href="registry-values-for-debugging-kmdf-drivers.md" data-raw-source="[ForceLogsInMiniDump](registry-values-for-debugging-kmdf-drivers.md)">ForceLogsInMiniDump</a> is set in the registry, or if the framework can determine that your driver caused the bug check.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevext" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdevext&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevext)"><strong>!wdfkd.wdfdevext</strong></a></p></td>
<td align="left"><p>Displays the WDFDEVICE-typed object handle that is associated with the <strong>DeviceExtension</strong> member of a Microsoft Windows Driver Model (WDM) <a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_device_object" data-raw-source="[&lt;strong&gt;DEVICE_OBJECT&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_device_object)"><strong>DEVICE_OBJECT</strong></a> structure.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 1</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevice" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdevice&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevice)"><strong>!wdfkd.wdfdevice</strong></a></p></td>
<td align="left"><p>Displays information that is associated with a WDFDEVICE-typed handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdeviceinterrupts" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdeviceinterrupts&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdeviceinterrupts)"><strong>!wdfkd.wdfdeviceinterrupts</strong></a></p></td>
<td align="left"><p>Displays all the interrupt objects for a specified device handle</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevicequeues" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdevicequeues&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdevicequeues)"><strong>!wdfkd.wdfdevicequeues</strong></a></p></td>
<td align="left"><p>Displays information about all of the queue objects that belong to a specified device.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmaenabler" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdmaenabler&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmaenabler)"><strong>!wdfkd.wdfdmaenabler</strong></a></p></td>
<td align="left"><p>Displays information about a <a href="framework-dma-objects.md" data-raw-source="[DMA enabler object](framework-dma-objects.md)">DMA enabler object</a>, along with its associated DMA transaction objects and common buffer objects.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmaenablers" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdmaenablers&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmaenablers)"><strong>!wdfkd.wdfdmaenablers</strong></a></p></td>
<td align="left"><p>Displays a summary of all DMA enabler objects, DMA transaction objects, and common buffer objects that are associated with a specified device object.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmatransaction" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdmatransaction&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmatransaction)"><strong>!wdfkd.wdfdmatransaction</strong></a></p></td>
<td align="left"><p>Displays information about a WDF direct memory access (DMA) transaction object.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdriverinfo" data-raw-source="[&lt;strong&gt;!wdfkd.wdfdriverinfo&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdriverinfo)"><strong>!wdfkd.wdfdriverinfo</strong></a></p></td>
<td align="left"><p>Displays information about a framework-based driver, such as its library version and hierarchy of object handles.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfextendwatchdog" data-raw-source="[&lt;strong&gt;!wdfkd.wdfextendwatchdog&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfextendwatchdog)"><strong>!wdfkd.wdfextendwatchdog</strong></a></p></td>
<td align="left"><p>Extends the time-out period (from 10 minutes to 24 hours) of the framework's watchdog timer during power transitions.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdffindobjects" data-raw-source="[&lt;strong&gt;!wdfkd.wdffindobjects&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdffindobjects)"><strong>!wdfkd.wdffindobjects</strong></a></p></td>
<td align="left"><p>Finds and displays framework objects.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfforwardprogress" data-raw-source="[&lt;strong&gt;!wdfkd.wdfforwardprogress&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfforwardprogress)"><strong>!wdfkd.wdfforwardprogress</strong></a></p></td>
<td align="left"><p>Displays information about the <a href="guaranteeing-forward-progress-of-i-o-operations.md" data-raw-source="[guaranteed forward progress](guaranteeing-forward-progress-of-i-o-operations.md)">guaranteed forward progress</a> capabilities of an I/O queue.</p></td>
<td align="left">KMDF</td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfgetdriver" data-raw-source="[&lt;strong&gt;!wdfkd.wdfgetdriver&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfgetdriver)"><strong>!wdfkd.wdfgetdriver</strong></a></p></td>
<td align="left"><p>Displays the driver name.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfhandle" data-raw-source="[&lt;strong&gt;!wdfkd.wdfhandle&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfhandle)"><strong>!wdfkd.wdfhandle</strong></a></p></td>
<td align="left"><p>Displays information about a framework object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfinterrupt" data-raw-source="[&lt;strong&gt;!wdfkd.wdfinterrupt&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfinterrupt)"><strong>!wdfkd.wdfinterrupt</strong></a></p></td>
<td align="left"><p>Displays information about a framework interrupt object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfiotarget" data-raw-source="[&lt;strong&gt;!wdfkd.wdfiotarget&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfiotarget)"><strong>!wdfkd.wdfiotarget</strong></a></p></td>
<td align="left"><p>Displays information about a WDFIOTARGET-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfldr" data-raw-source="[&lt;strong&gt;!wdfkd.wdfldr&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfldr)"><strong>!wdfkd.wdfldr</strong></a></p></td>
<td align="left"><p>Displays information about all of the drivers that are using the framework library.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 1</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdflogdump" data-raw-source="[&lt;strong&gt;!wdfkd.wdflogdump&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdflogdump)"><strong>!wdfkd.wdflogdump</strong></a></p></td>
<td align="left"><p>Displays the framework's event log records, if available, from a complete memory dump, a kernel memory dump, or a live kernel-mode target.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdflogsave" data-raw-source="[&lt;strong&gt;!wdfkd.wdflogsave&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdflogsave)"><strong>!wdfkd.wdflogsave</strong></a></p></td>
<td align="left"><p>Saves the framework's event log records in an event trace log (.<em>etl</em>) file that you can view by using <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/traceview" data-raw-source="[TraceView](https://docs.microsoft.com/windows-hardware/drivers/devtest/traceview)">TraceView</a>.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfmemory" data-raw-source="[&lt;strong&gt;!wdfkd.wdfmemory&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfmemory)"><strong>!wdfkd.wdfmemory</strong></a></p></td>
<td align="left"><p>Displays a memory object's buffer address and size.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfobject" data-raw-source="[&lt;strong&gt;!wdfkd.wdfobject&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfobject)"><strong>!wdfkd.wdfobject</strong></a></p></td>
<td align="left"><p>Displays information about a framework object.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfopenhandles" data-raw-source="[&lt;strong&gt;!wdfkd.wdfopenhandles&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfopenhandles)"><strong>!wdfkd.wdfopenhandles</strong></a></p></td>
<td align="left"><p>Displays information about all the handles that are open on the specified WDF device.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfpoolusage" data-raw-source="[&lt;strong&gt;!wdfkd.wdfpoolusage&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfpoolusage)"><strong>!wdfkd.wdfpoolusage</strong></a></p></td>
<td align="left"><p>Displays a driver's memory pool usage.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfqueue" data-raw-source="[&lt;strong&gt;!wdfkd.wdfqueue&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfqueue)"><strong>!wdfkd.wdfqueue</strong></a></p></td>
<td align="left"><p>Displays information about a WDFQUEUE-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfrequest" data-raw-source="[&lt;strong&gt;!wdfkd.wdfrequest&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfrequest)"><strong>!wdfkd.wdfrequest</strong></a></p></td>
<td align="left"><p>Displays information about a WDFREQUEST-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsearchpath" data-raw-source="[&lt;strong&gt;!wdfkd.wdfsearchpath&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsearchpath)"><strong>!wdfkd.wdfsearchpath</strong></a></p></td>
<td align="left"><p>Sets the search path for locating the framework log's format files.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsettraceprefix" data-raw-source="[&lt;strong&gt;!wdfkd.wdfsettraceprefix&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsettraceprefix)"><strong>!wdfkd.wdfsettraceprefix</strong></a></p></td>
<td align="left"><p>Sets a prefix string for tracing messages in the framework's event log.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsetdriver" data-raw-source="[&lt;strong&gt;!wdfkd.wdfsetdriver&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfsetdriver)"><strong>!wdfkd.wdfsetdriver</strong></a></p></td>
<td align="left"><p>Sets a driver name that is used as a default name for other commands that require a driver name.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfspinlock" data-raw-source="[&lt;strong&gt;!wdfkd.wdfspinlock&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfspinlock)"><strong>!wdfkd.wdfspinlock</strong></a></p></td>
<td align="left"><p>Displays information about a framework spin-lock object. This information includes the spin lock's acquisition history and the length of time that the lock was held.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftagtracker" data-raw-source="[&lt;strong&gt;!wdfkd.wdftagtracker&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftagtracker)"><strong>!wdfkd.wdftagtracker</strong></a></p></td>
<td align="left"><p>Displays tag information (including the tag value, line, file, and time) for a specified object tag.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftmffile" data-raw-source="[&lt;strong&gt;!wdfkd.wdftmffile&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftmffile)"><strong>!wdfkd.wdftmffile</strong></a></p></td>
<td align="left"><p>Specifies the trace message format (.<em>tmf</em>) files that the <strong>!wdflogdump</strong> extension will use to display event log records.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftraceprtdebug" data-raw-source="[&lt;strong&gt;!wdfkd.wdftraceprtdebug&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdftraceprtdebug)"><strong>!wdfkd.wdftraceprtdebug</strong></a></p></td>
<td align="left"><p>Turns on the TracePrt diagnostic mode.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdevstack" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumdevstack&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdevstack)"><strong>!wdfkd.wdfumdevstack</strong></a></p></td>
<td align="left"><p>Displays detailed information about a UMDF device stack in the implicit process.</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdevstacks" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumdevstacks&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdevstacks)"><strong>!wdfkd.wdfumdevstacks</strong></a></p></td>
<td align="left"><p>Displays information about all UMDF device stacks in the implicit process.</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdownirp" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumdownirp&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumdownirp)"><strong>!wdfkd.wdfumdownirp</strong></a></p></td>
<td align="left"><p>Displays the kernel-mode I/O request packet (IRP) that is associated with a specified user-mode IRP.</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumfile" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumfile&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumfile)"><strong>!wdfkd.wdfumfile</strong></a></p></td>
<td align="left"><p>Displays information about a UMDF intra-stack file.</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirp" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumirp&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirp)"><strong>!wdfkd.wdfumirp</strong></a></p></td>
<td align="left"><p>Displays information about a user-mode I/O request packet (UM IRP).</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirps" data-raw-source="[&lt;strong&gt;!wdfkd.wdfumirps&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfumirps)"><strong>!wdfkd.wdfumirps</strong></a></p></td>
<td align="left"><p>Displays the list of pending user-mode I/O request packets (UM IRPs) in the implicit process.</p></td>
<td align="left"><p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbdevice" data-raw-source="[&lt;strong&gt;!wdfkd.wdfusbdevice&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbdevice)"><strong>!wdfkd.wdfusbdevice</strong></a></p></td>
<td align="left"><p>Displays information about a WDFUSBDEVICE-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbinterface" data-raw-source="[&lt;strong&gt;!wdfkd.wdfusbinterface&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbinterface)"><strong>!wdfkd.wdfusbinterface</strong></a></p></td>
<td align="left"><p>Displays information about a WDFUSBINTERFACE-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbpipe" data-raw-source="[&lt;strong&gt;!wdfkd.wdfusbpipe&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfusbpipe)"><strong>!wdfkd.wdfusbpipe</strong></a></p></td>
<td align="left"><p>Displays information about a WDFUSBPIPE-typed object handle.</p></td>
<td align="left"><p>KMDF</p>
<p>UMDF 2</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfwmi" data-raw-source="[&lt;strong&gt;!wdfkd.wdfwmi&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfwmi)"><strong>!wdfkd.wdfwmi</strong></a></p></td>
<td align="left"><p>Displays a device's Windows Management Instrumentation (WMI) information.</p></td>
<td align="left">KMDF</td>
</tr>
</tbody>
</table>

 

 

 





