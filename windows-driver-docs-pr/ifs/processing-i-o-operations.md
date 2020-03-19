---
title: Processing I/O Operations
description: Processing I/O Operations
ms.assetid: 750fa89b-dbdf-45ff-bfa5-83c717d2d7bb
keywords:
- filter manager WDK file system minifilter , processing I/O operations
- preoperation callback routines WDK file system minifilter , filter manager
- postoperation callback routines WDK file system minifilter , filter manager
- opportunistic lock WDK file system minifilter
- locking WDK file system minifilter
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Processing I/O Operations


The filter manager simplifies processing I/O operations for minifilter drivers. Unlike a legacy filter driver, which must correctly pass all I/O requests to the next-lower driver and correctly handle pending requests, synchronization, and I/O completion whether the legacy filter driver does any work related to the request, a minifilter driver registers only for the I/O operations it must handle.

For a given I/O operation, the filter manager calls only minifilter drivers that have registered a [**preoperation callback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_pre_operation_callback) routine for that operation. The filter manager also handles certain IRP maintenance tasks on behalf of the minifilter driver, such as copying parameters to the next stack location and propagating the IRP **PendingReturned** flag.

In its preoperation callback routine, a minifilter driver does whatever processing is needed for the I/O operation and indicates what should be done to the IRP by returning the appropriate value from its preoperation callback routine. For example, to forward an IRP to the next-lower driver without a completion routine, the minifilter driver returns FLT\_PREOP\_SUCCESS\_NO\_CALLBACK; to do the same with a completion routine (the minifilter driver's postoperation callback routine for the I/O operation), the minifilter driver returns FLT\_PREOP\_SUCCESS\_WITH\_CALLBACK.

In its preoperation callback routine, the minifilter driver can queue the operation to a worker thread if needed by calling [**FltQueueDeferredIoWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltqueuedeferredioworkitem). After doing so, the minifilter driver returns FLT\_PREOP\_PENDING from its preoperation callback routine to indicate that the I/O operation is pending, and the minifilter driver is responsible for completing or resuming processing of the request. To resume processing, the minifilter driver calls [**FltCompletePendedPreOperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcompletependedpreoperation) from the worker thread.

If the minifilter driver needs to maintain its own per-instance cancel-safe queue of outstanding I/O operations to be processed, it can set up such a queue by calling [*FltCbdqInitialize*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqinitialize) in its *InstanceSetupCallback* routine and calling [*FltCbdqInsertIo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqinsertio) in its preoperation callback routine as needed to insert I/O operations into the queue.

The filter manager calls a minifilter driver's [**postoperation callback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_post_operation_callback) routine for an I/O operation when lower filter drivers (legacy filters and minifilter drivers) have finished completion processing.

In its postoperation callback routine, the minifilter driver can call [**FltDoCompletionProcessingWhenSafe**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltdocompletionprocessingwhensafe) to ensure that completion processing is performed at safe IRQL. Or it can queue the completion processing of the operation to a worker thread if needed by calling [**FltQueueDeferredIoWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltqueuedeferredioworkitem). After doing so, the minifilter driver returns FLT\_POSTOP\_MORE\_PROCESSING\_REQUIRED from its postoperation callback routine to halt the filter manager's completion processing for the I/O operation. To resume completion processing, the minifilter driver calls [**FltCompletePendedPostOperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcompletependedpostoperation) from the worker thread.

The filter manager provides support for queuing of "generic" work items - work items that are associated with a minifilter driver or minifilter driver instance rather than an I/O operation. A minifilter driver can insert a work item into a system work queue by calling [**FltQueueGenericWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltqueuegenericworkitem). This routine is similar to routines such as [**ExQueueWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exqueueworkitem); for example, work items (allocated by calling [**FltAllocateGenericWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocategenericworkitem)) can be reused. However, **FltQueueGenericWorkItem** is safer for minifilter drivers to use, because the filter manager does not allow the minifilter driver or minifilter driver instance to unload while outstanding work items are still being processed.

The filter manager also provides support for opportunistic lock (oplock) operations. For oplock operations, a minifilter driver can use such filter manager routines as [**FltInitializeOplock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltinitializeoplock) and [**FltOplockFsctrl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltoplockfsctrl), which are equivalent to the **FsRtlInitializeOplock** and **FsRtlOplockFsctrl** routines that are used by file systems and legacy filter drivers.

### <span id="Filter_Manager_Routines_for_Processing_I_O_Operations"></span><span id="filter_manager_routines_for_processing_i_o_operations"></span><span id="FILTER_MANAGER_ROUTINES_FOR_PROCESSING_I_O_OPERATIONS"></span>Filter Manager Routines for Processing I/O Operations

The filter manager provides the following support routines for pending I/O in [**preoperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_pre_operation_callback) and [**postoperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_post_operation_callback) callback routines:

[**FltCompletePendedPostOperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcompletependedpostoperation)

[**FltCompletePendedPreOperation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcompletependedpreoperation)

[**FltDoCompletionProcessingWhenSafe**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltdocompletionprocessingwhensafe)

The following routines are used for queuing work items in preoperation and postoperation callback routines:

[**FltAllocateDeferredIoWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocatedeferredioworkitem)

[**FltAllocateGenericWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltallocategenericworkitem)

[**FltFreeDeferredIoWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfreedeferredioworkitem)

[**FltFreeGenericWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfreegenericworkitem)

[**FltQueueDeferredIoWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltqueuedeferredioworkitem)

[**FltQueueGenericWorkItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltqueuegenericworkitem)

The following routines provide cancel-safe queue support:

[*FltCbdqDisable*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqdisable)

[*FltCbdqEnable*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqenable)

[*FltCbdqInitialize*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqinitialize)

[*FltCbdqInsertIo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqinsertio)

[*FltCbdqRemoveIo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqremoveio)

[*FltCbdqRemoveNextIo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcbdqremovenextio)

The following routines provide oplock support:

[*FltCheckOplock*](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcheckoplock)

[**FltCurrentBatchOplock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltcurrentbatchoplock)

[**FltInitializeOplock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltinitializeoplock)

[**FltOplockFsctrl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltoplockfsctrl)

[**FltOplockIsFastIoPossible**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltoplockisfastiopossible)

[**FltUninitializeOplock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltuninitializeoplock)

### <span id="Minifilter_Driver_Callback_Routines_for_Processing_I_O_Operations"></span><span id="minifilter_driver_callback_routines_for_processing_i_o_operations"></span><span id="MINIFILTER_DRIVER_CALLBACK_ROUTINES_FOR_PROCESSING_I_O_OPERATIONS"></span>Minifilter Driver Callback Routines for Processing I/O Operations

The following callback routines are stored in the [**FLT\_OPERATION\_REGISTRATION**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_operation_registration) structure for each type of I/O operation that the minifilter driver handles:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Callback Routine Name</th>
<th align="left">Callback Routine Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>PostOperation</em></p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_post_operation_callback" data-raw-source="[&lt;strong&gt;PFLT_POST_OPERATION_CALLBACK&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_post_operation_callback)"><strong>PFLT_POST_OPERATION_CALLBACK</strong></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><em>PreOperation</em></p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_pre_operation_callback" data-raw-source="[&lt;strong&gt;PFLT_PRE_OPERATION_CALLBACK&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_pre_operation_callback)"><strong>PFLT_PRE_OPERATION_CALLBACK</strong></a></p></td>
</tr>
</tbody>
</table>

 

 

 




