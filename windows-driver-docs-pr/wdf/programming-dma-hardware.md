---
title: Programming DMA Hardware
description: This topic describes the functionality that a KMDF driver for a bus-master DMA device typically provides in its EvtProgramDma event callback function.
ms.assetid: 5e74fe74-d38f-4cca-b0cf-8a6f170c4dc5
keywords:
- DMA operations WDK KMDF , transfers
- bus-master DMA WDK KMDF , transfers
- DMA transfers WDK KMDF , hardware
- DMA transfers WDK KMDF , starting
- starting DMA transfers WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Programming DMA Hardware


\[Applies to KMDF only\]

This topic describes the functionality that a KMDF driver for a bus-master DMA device typically provides in its [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) event callback function. If your driver uses the framework's DMA support, the driver must provide this callback. This information also applies to a KMDF driver for a [system-mode DMA device](supporting-system-mode-dma.md) that has a hardware interrupt.




The [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) callback function, which is called at IRQL = DISPATCH\_LEVEL, programs the device to start a [DMA transfer](dma-transactions-and-dma-transfers.md). The input parameters for this callback function supply the transfer's direction (input or output) and a scatter/gather list. If the transfer consists of a single packet, the scatter/gather list contains a single element.

The [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) callback function programs the device by using the hardware resources that the driver's [*EvtDevicePrepareHardware*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_prepare_hardware) callback function received. If the *EvtProgramDma* callback function successfully programs the hardware, it returns **TRUE**.

After the hardware has completed the DMA transfer, typically the hardware issues an interrupt and the system calls the driver's [*EvtInterruptIsr*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_isr) callback function. The driver's *EvtInterruptIsr* callback function usually:

-   Clears the hardware interrupt.

-   Saves the interrupt's context information if it is needed. This information might be lost after the callback function returns and the system lowers the IRQL (because lowering the IRQL allows additional interrupts to occur).

-   Calls [**WdfInterruptQueueDpcForIsr**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nf-wdfinterrupt-wdfinterruptqueuedpcforisr) to schedule an [*EvtInterruptDpc*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_dpc) callback function.

The [*EvtInterruptDpc*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_dpc) callback function [completes the DMA transfer](completing-a-dma-transfer.md) by using context information that the [*EvtInterruptIsr*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_isr) callback function saved.

If the [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) callback function detects an error, the driver can stop the transaction.

To stop a transaction when the driver detects an error, the [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) callback function must:

1.  Call [**WdfDmaTransactionDmaCompletedFinal**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactiondmacompletedfinal).

2.  Call [**WdfObjectDelete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/nf-wdfobject-wdfobjectdelete) to delete the DMA transaction object, or call [**WdfDmaTransactionRelease**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionrelease) to release and reuse the DMA transaction object.

3.  [Requeue the I/O request](requeuing-i-o-requests.md) or [complete the I/O request](completing-i-o-requests.md), if the transaction is associated with a framework request object. To retrieve a handle to the request, the driver can call [**WdfDmaTransactionGetRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactiongetrequest).

4.  Return **FALSE**.

Steps 1 and 4 are illustrated in the following code example, taken from the [PLX9x5x](https://go.microsoft.com/fwlink/p/?linkid=256157) sample’s [*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma) callback function for read requests in the *Read.c* file.

```cpp
    // If errors occur in the EvtProgramDma callback,
    // release the DMA transaction object and complete the request.

    if (errors) {
        NTSTATUS status;

        //
        // Must abort the transaction before deleting.
        //
        (VOID) WdfDmaTransactionDmaCompletedFinal(Transaction, 0, &status);
        ASSERT(NT_SUCCESS(status));

        PLxReadRequestComplete( Transaction, STATUS_INVALID_DEVICE_STATE );
        TraceEvents(TRACE_LEVEL_ERROR, DBG_READ,
                    "<-- PLxEvtProgramReadDma: errors ****");
        return FALSE;
    }
```

The example calls the **PLxReadRequestComplete** function to perform steps 2 and 3:

```cpp
VOID
PLxReadRequestComplete(
    IN WDFDMATRANSACTION  DmaTransaction,
    IN NTSTATUS           Status
    )
/*++

Routine Description:

Arguments:

Return Value:

--*/
{
    WDFREQUEST         request;
    size_t             bytesTransferred;

    //
    // Get the associated request from the transaction.
    //
    request = WdfDmaTransactionGetRequest(DmaTransaction);

    ASSERT(request);

    //
    // Get the final bytes transferred count.
    //
    bytesTransferred =  WdfDmaTransactionGetBytesTransferred( DmaTransaction );

    TraceEvents(TRACE_LEVEL_INFORMATION, DBG_DPC,
                "PLxReadRequestComplete:  Request %p, Status %!STATUS!, "
                "bytes transferred %d\n",
                 request, Status, (int) bytesTransferred );

    WdfDmaTransactionRelease(DmaTransaction);

    //
    // Complete this Request.
    //
    WdfRequestCompleteWithInformation( request, Status, bytesTransferred);

}
```









