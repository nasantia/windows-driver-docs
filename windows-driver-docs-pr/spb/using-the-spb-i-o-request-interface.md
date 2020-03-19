---
title: Using the SPB I/O Request Interface
description: Starting with Windows 8, the SPB framework extension (SpbCx) is a system-supplied component that supports the SPB I/O request interface.
ms.assetid: 0A752413-FA0B-4C26-BF6D-19033E07095E
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Using the SPB I/O Request Interface

Starting with Windows 8, the [SPB framework extension](https://docs.microsoft.com/windows-hardware/drivers/spb/spb-framework-extension) (SpbCx) is a system-supplied component that supports the [SPB I/O request interface](https://docs.microsoft.com/previous-versions/hh698224(v=vs.85)). SPB peripheral device drivers use this interface to send I/O requests to devices that are connected to I²C, SPI, and other [simple peripheral buses](https://docs.microsoft.com/previous-versions/hh450903(v=vs.85)) (SPBs). By making a standardized I/O request interface available across a variety of bus types, SpbCx simplifies the task of providing driver support for a family of peripheral devices across a variety of hardware platforms and SPB controllers from different hardware vendors.

If the following conditions are met, the hardware vendor for an SPB-connected peripheral device can develop one device driver that can work across multiple bus types:

- The peripheral device must be hardware-compatible with these buses.
- The driver can use the same device-control protocols across all of these bus types.

By eliminating bus-specific code from peripheral drivers, the SPB framework extension shortens development time for these drivers and ensures more consistent behavior across the supported bus types.

Peripheral devices that are connected to SPBs are not memory-mapped, and the drivers for these devices cannot directly access the hardware registers of these devices. Instead, an SPB peripheral device driver must rely on an SPB controller to serially transfer data to and from the device. To request such a transfer, the driver must send an I/O request to the device. This I/O request is sent to a queue that is managed by SpbCx.

SpbCx cooperates with an SPB controller driver to handle I/O requests from drivers. The hardware vendor for the SPB controller supplies the SPB controller driver to perform tasks that are specific to the controller hardware.

Only drivers can send I/O requests to the I/O request interface of an SPB controller. Applications cannot directly send I/O requests to an SPB controller. Instead, an application can send I/O requests to the driver for an SPB-connected peripheral device, and then rely on the driver to send the SPB controller any I/O requests that might be required to transfer data to or from the device.

Before a driver can send I/O requests to an SPB-connected peripheral device, the driver must open a open a logical connection to the device. To open this connection, the driver uses the connection ID that it received as a hardware resource from the Plug and Play manager. For more information, see [Connection IDs for SPB Peripheral Devices](https://docs.microsoft.com/windows-hardware/drivers/spb/connection-ids-for-spb-connected-peripheral-devices).

SpbCx and the SPB controller driver jointly handle read and write requests for SPB-connected peripheral devices. In response to an [**IRP\_MJ\_READ**](https://docs.microsoft.com/previous-versions/ff546883(v=vs.85)) request, the SPB controller transfers the specified number of bytes from a peripheral device to a driver-supplied buffer. In response to an [**IRP\_MJ\_WRITE**](https://docs.microsoft.com/previous-versions//ff546904(v=vs.85)) request, the SPB controller transfers the specified number of bytes from a driver-supplied buffer to a peripheral device.

For an **IRP\_MJ\_READ** or **IRP\_MJ\_WRITE** request to transfer zero bytes, SpbCx completes the request with a STATUS\_SUCCESS status code, but performs no operation.

SpbCx and the SPB controller driver also handle these SPB-specific I/O control codes (IOCTLs):

- [**IOCTL\_SPB\_EXECUTE\_SEQUENCE**](https://docs.microsoft.com/windows-hardware/drivers/spb/spb-ioctls#ioctl-spb-execute-sequence)
- [**IOCTL\_SPB\_LOCK\_CONTROLLER**](https://docs.microsoft.com/windows-hardware/drivers/spb/spb-ioctls#ioctl-spb-lock-controller)
- [**IOCTL\_SPB\_UNLOCK\_CONTROLLER**](https://docs.microsoft.com/windows-hardware/drivers/spb/spb-ioctls#ioctl_spb_unlock_controller-control-code)

An SPB peripheral driver uses these IOCTLs to perform *I/O transfer sequences*. An I/O transfer sequence is an ordered set of bus transfers (read and write operations) that is performed as a single, atomic bus operation. For more information about these IOCTLs, see [I/O Transfer Sequences](https://docs.microsoft.com/windows-hardware/drivers/spb/i-o-transfer-sequences).

The SPB controller driver for a particular SPB controller might support custom IOCTLs that perform hardware-specific functions. These are IOCTLs that SpbCx does not handle and that the hardware vendor for the SPB controller supports for the benefit of SPB peripheral device drivers that need to perform hardware-specific operations. If an SPB peripheral device driver sends an IOCTL that neither SpbCx nor the SPB controller driver recognizes, no operation is performed and the I/O request is completed with an error status value of STATUS\_NOT\_SUPPORTED.

The driver for an SPB-connected peripheral device is typically either a [User-Mode Driver Framework](https://docs.microsoft.com/windows-hardware/drivers/wdf/overview-of-the-umdf) (UMDF) driver or [Kernel-Mode Driver Framework](https://docs.microsoft.com/windows-hardware/drivers/wdf/index) (KMDF) driver. To send a read, write, or IOCTL request to an SPB-connected peripheral device, a UMDF driver calls a method such as [**IWDFIoRequest::Send**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfiorequest-send). A KMDF driver calls a method such as [**WdfIoTargetSendReadSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetsendreadsynchronously), [**WdfIoTargetSendWriteSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetsendwritesynchronously), or [**WdfIoTargetSendIoctlSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetsendioctlsynchronously).

For code examples that show how to send I/O requests to SPB-connected peripheral devices, see these topics:

[Hardware Resources for User-Mode SPB Peripheral Drivers](https://docs.microsoft.com/windows-hardware/drivers/spb/hardware-resources-for-user-mode-spb-peripheral-drivers)

[Hardware Resources for Kernel-Mode SPB Peripheral Drivers](https://docs.microsoft.com/windows-hardware/drivers/spb/hardware-resources-for-kernel-mode-spb-peripheral-drivers)
