---
title: Programming Considerations for USBPRINT
description: Programming Considerations for USBPRINT
ms.assetid: 351b3124-d584-4817-a5ce-09e16b54d41b
keywords:
- printer drivers WDK , USB
- USBPRINT
- USBMON
- USB printers WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Programming Considerations for USBPRINT





Usbprint.sys, together with USBMON, provides an interface very similar to that used by parallel printers. In many cases, it is possible for a single printer driver or language monitor to work correctly on both parallel and USB printers without modification. If a language monitor uses only the [**WritePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-writeport) and [**ReadPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-readport) functions and the [**IOCTL\_PAR\_QUERY\_DEVICE\_ID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddpar/ni-ntddpar-ioctl_par_query_device_id) request, it will be portable between USB and parallel printers.

In some cases, it might be necessary for a language monitor to make vendor-specific requests to a printer in order to take advantage of special printer features. To do this, use [**IOCTL\_USBPRINT\_VENDOR\_SET\_COMMAND**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_vendor_set_command) and [**IOCTL\_USBPRINT\_VENDOR\_GET\_COMMAND**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_vendor_get_command). Note, however, that using these IOCTLs renders a language monitor incompatible with the parallel port monitor.

Language monitors normally do not have access to a device handle for the printer they are managing. Instead, they have a port name provided by the port monitor that sits between the language monitor and the bus driver (Usbprint.sys in this case). See [Language and Port Monitor Interaction](language-and-port-monitor-interaction.md) for more information. The lack of a device handle prevents language monitors from directly calling device bus driver IOCTLs. To overcome this limitation, USBMON implements the [**GetPrinterDataFromPort**](https://docs.microsoft.com/previous-versions/ff550506(v=vs.85)) API, which allows language monitors to issue IOCTLs through USBMON to USBPRINT.

The USB printing stack shares the following APIs and IOCTL with the parallel printing stack:

[**WritePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-writeport)

[**ReadPort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winsplp/nf-winsplp-readport)

[**IOCTL\_PAR\_QUERY\_DEVICE\_ID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddpar/ni-ntddpar-ioctl_par_query_device_id)

The following IOCTLs are specific to the USB printing stack:

[**IOCTL\_USBPRINT\_GET\_1284\_ID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_get_1284_id)

[**IOCTL\_USBPRINT\_GET\_LPT\_STATUS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_get_lpt_status)

[**IOCTL\_USBPRINT\_SOFT\_RESET**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_soft_reset)

[**IOCTL\_USBPRINT\_VENDOR\_GET\_COMMAND**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_vendor_get_command)

[**IOCTL\_USBPRINT\_VENDOR\_SET\_COMMAND**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbprint/ni-usbprint-ioctl_usbprint_vendor_set_command)

**Note**   Usbprint.sys does not provide a mechanism for obtaining descriptors from the device, nor for directly manipulating USB pipes.

 

 

 




