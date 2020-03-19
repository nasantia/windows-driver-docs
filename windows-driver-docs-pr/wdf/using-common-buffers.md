---
title: Using Common Buffers
description: Using Common Buffers
ms.assetid: 81a56f62-917e-4798-b2cc-6469c802fab8
keywords:
- DMA operations WDK KMDF , common buffers
- bus-master DMA WDK KMDF , common buffers
- common buffers WDK KMDF
- buffers WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Using Common Buffers


\[Applies to KMDF only\]




Drivers for DMA devices sometimes must allocate buffer space that both a device and the driver can access. For example, a device might write transfer information, such as byte counts, into this buffer space and the driver can read it to determine the number of bytes that were transferred. This type of buffer space is called a *common buffer*.

To allocate a common buffer, your driver's [*EvtDriverDeviceAdd*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/nc-wdfdriver-evt_wdf_driver_device_add) callback function:

-   Calls [**WdfDmaEnablerCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/nf-wdfdmaenabler-wdfdmaenablercreate) to create a DMA enabler object.

-   Calls [**WdfCommonBufferCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffercreate) or [**WdfCommonBufferCreateWithConfig**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffercreatewithconfig) to create the buffer.

-   Calls [**WdfCommonBufferGetAlignedLogicalAddress**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffergetalignedlogicaladdress) to obtain the buffer's logical address, which the device can access.

-   Calls [**WdfCommonBufferGetAlignedVirtualAddress**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffergetalignedvirtualaddress) to obtain the buffer's virtual address, which the driver can access.

The following code example is taken from the *Init.c* file of the [PLX9x5x](https://go.microsoft.com/fwlink/p/?linkid=256157) sample. This code shows how a KMDF driver allocates common buffer space.

```cpp
// Allocate common buffer for building writes
DevExt->WriteCommonBufferSize = 
         sizeof( DMA_TRANSFER_ELEMENT) * DevExt->WriteTransferElements;
status = WdfCommonBufferCreate( DevExt->DmaEnabler,
                                DevExt->WriteCommonBufferSize,
                                WDF_NO_OBJECT_ATTRIBUTES, 
                                &DevExt->WriteCommonBuffer );
if (!NT_SUCCESS(status)) {
    . . . //Error-handling code omitted 
    }
DevExt->WriteCommonBufferBase = 
             WdfCommonBufferGetAlignedVirtualAddress(
                      DevExt->WriteCommonBuffer);
DevExt->WriteCommonBufferBaseLA = 
             WdfCommonBufferGetAlignedLogicalAddress(
                      DevExt->WriteCommonBuffer);
RtlZeroMemory( DevExt->WriteCommonBufferBase, DevExt->WriteCommonBufferSize);
```

If your driver calls [**WdfDeviceSetAlignmentRequirement**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicesetalignmentrequirement) before calling [**WdfDmaEnablerCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/nf-wdfdmaenabler-wdfdmaenablercreate), the buffers that **WdfDmaEnablerCreate** creates are aligned to the memory address boundary that the driver specified to **WdfDeviceSetAlignmentRequirement**. Otherwise, common buffers are aligned to word address boundaries. Alternatively, the driver can call [**WdfCommonBufferCreateWithConfig**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffercreatewithconfig) to specify an alignment for a single buffer.

To obtain the length of a common buffer that your driver has allocated, the driver can call [**WdfCommonBufferGetLength**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffergetlength).

When the driver is finished using a common buffer, the driver calls [**WdfObjectDelete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/nf-wdfobject-wdfobjectdelete).









