---
title: KMDF Version History
description: This topic lists versions of Kernel-Mode Driver Framework (KMDF), the corresponding versions of the Windows operating system, and the changes made in each release.
ms.assetid: b920937c-2e5d-48cc-81b5-1462f5d03d75
keywords:
- kernel-mode drivers WDK KMDF , revision history
- KMDF WDK , revision history
- Kernel-Mode Driver Framework WDK , revision history
ms.date: 10/02/2018
ms.localizationpriority: medium
ms.custom: 19H1
---

# KMDF Version History


This topic lists versions of Kernel-Mode Driver Framework (KMDF), the corresponding versions of the Windows operating system, and the changes made in each release.

The following table shows the release history of the KMDF library:

|KMDF version|Release method|Included in this version of Windows|Drivers using it run on|
|--- |--- |--- |--- |
|1.29|Not released in WDK|Windows 10, version 1903 (March 2019 Update, 19H1)|Windows 10, version 1903 and later|
|1.27|Windows 10, version 1809 WDK|Windows 10, version 1809 (October 2018 Update, Redstone 5)|Windows 10, version 1809 and later|
|1.25|Windows 10, version 1803 WDK|Windows 10, version 1803 (April 2018 Update, Redstone 4)|Windows 10, version 1803 and later|
|1.23|Windows 10, version 1709 WDK|Windows 10, version 1709 (Fall Creators Update, Redstone 3)|Windows 10, version 1709 and later|
|1.21|Windows 10, version 1703 WDK|Windows 10, version 1703 (Creators Update, Redstone 2)|Windows 10, version 1703 and later|
|1.19|Windows 10, version 1607 WDK|Windows 10, version 1607 (Anniversary Update, Redstone 1)|Windows 10 version 1607, Windows Server 2016 and later|
|1.17|Windows 10, version 1511 WDK|Windows 10, version 1511 (November Update, Threshold 2)|Windows 10 version 1511, Windows Server 2016 and later|
|1.15|Windows 10 WDK|Windows 10, version 1507 (Threshold 1)|Windows 10, version 1507, Windows Server 2016 and later|
|1.13|Windows 8.1 WDK|Windows 8.1|Windows 8.1 and later|
|1.11|Windows 8 WDK|Windows 8|Windows Vista and later|
|1.9|Windows 7 WDK|Windows 7|Windows XP and later|
|1.7|Windows Server 2008 WDK|Windows Vista with Service Pack 1 (SP1), Windows Server 2008|Windows 2000 and later|
|1.5|Windows Vista WDK|Windows Vista|Windows 2000 and later|
|1.1|Download only|None|Windows 2000 and later|
|1.0|Download only|None|Windows XP and later|

You can use the Windows Driver Kit (WDK) with Microsoft Visual Studio 2017 to build drivers that run on Windows 7 and later.

For help determining what version of WDF to use, see [Which framework version should I use?](building-and-loading-a-kmdf-driver.md#which-framework-version-should-i-use).

For a complete list of callbacks and methods, and which frameworks and versions they apply to, see [Summary of WDF Callbacks and Methods](https://docs.microsoft.com/windows-hardware/drivers/ddi/_wdf/).

For information about the new features for KMDF drivers in Windows 10, see [What's New for WDF Drivers](index.md).

## KMDF Version 1.29

Unchanged from version 1.25.

## KMDF Version 1.27

Unchanged from version 1.25.

## KMDF Version 1.25

* [Building a WDF driver for multiple versions of Windows](building-a-wdf-driver-for-multiple-versions-of-windows.md)

## KMDF Version 1.23

* Companion functionality added for internal use only.  For the new DDIs, see [Summary of WDF Callbacks and Methods](https://docs.microsoft.com/windows-hardware/drivers/ddi/_wdf/).

## KMDF Version 1.21

* [**WdfFileObjectGetInitiatorProcessId**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffileobject/nf-wdffileobject-wdffileobjectgetinitiatorprocessid) was previously UMDF-only, now available in KMDF.
* [**WdfRequestGetRequestorProcessId**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestgetrequestorprocessid) was previously UMDF-only, now available in KMDF.
* [**WdfObjectDereferenceActual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/nf-wdfobject-wdfobjectdereferenceactual): Type of *File* parameter changed from PCHAR to PCCH.
* [**WdfObjectReferenceActual**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/nf-wdfobject-wdfobjectreferenceactual): Type of *File* parameter changed from PCHAR to PCCH.

## KMDF Version 1.19

* Added [**WdfDmaTransactionSetSingleTransferRequirement**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionsetsingletransferrequirement)
* Added **WDF_DMA_ENABLER_CONFIG_REQUIRE_SINGLE_TRANSFER** flag in [**WDF_DMA_ENABLER_CONFIG_FLAGS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/ne-wdfdmaenabler-_wdf_dma_enabler_config_flags)
* Added **STATUS_WDF_TOO_MANY_TRANSFERS** return value for [**WdfDmaTransactionInitialize**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactioninitialize) and [**WdfDmaTransactionDmaCompleted**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactiondmacompleted)
* Added output messages for single transfer output to [**!wdfkd.wdfdmatransaction**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmatransaction) and [**!wdfkd.wdfdmaenabler**](https://docs.microsoft.com/windows-hardware/drivers/debugger/-wdfkd-wdfdmaenabler)
* For more info about single transfer DMA, see [Using Single Transfer DMA](using-single-transfer-dma.md).

## KMDF Version 1.15

-   The new [**WdfDeviceOpenDevicemapKey**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceopendevicemapkey) method allows a driver to access subkeys and values under **HKEY\_LOCAL\_MACHINE\\HARDWARE\\DEVICEMAP**.

## KMDF Version 1.13


KMDF version 1.13 adds the following functionality:

-   Added **CanWakeDevice** member to [**WDF\_INTERRUPT\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/ns-wdfinterrupt-_wdf_interrupt_config) structure to support interrupts that can be used to bring a device from a low-power Dx state back to its fully on D0 state. For more information, see [Using an Interrupt to Wake a Device](using-an-interrupt-to-wake-a-device.md).
-   Support for high resolution timers. For more information, see [Using Timers](using-timers.md).
-   Support for timers that do not wake the system if they expire when the system is in a low-power state. For more information, see [Using Timers](using-timers.md).
-   The following KMDF/UMDF methods described in [Accessing the Unified Device Property Model](accessing-the-unified-device-property-model.md):
    -   [**WdfDeviceAllocAndQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceallocandquerypropertyex)
    -   [**WdfDeviceAssignProperty**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceassignproperty)
    -   [**WdfDeviceInitSetIoTypeEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceinitsetiotypeex)
    -   [**WdfDeviceQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicequerypropertyex)
    -   [**WdfFdoInitAllocAndQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nf-wdffdo-wdffdoinitallocandquerypropertyex)
    -   [**WdfFdoInitQueryPropertyEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdffdo/nf-wdffdo-wdffdoinitquerypropertyex)

For information about UMDF versions, see [UMDF Version History](umdf-version-history.md).

## KMDF Version 1.11


Version 1.11 adds the following functionality:

-   [System-mode DMA](supporting-system-mode-dma.md)

-   Support for [passive-level interrupts](supporting-passive-level-interrupts.md)

-   [Functional power states](supporting-functional-power-states.md) for multiple components within a single device

-   [Dispatching IRPs to I/O Queues](dispatching-irps-to-i-o-queues.md)
-   The following methods:
    -   [**WdfDeviceConfigureWdmIrpDispatchCallback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceconfigurewdmirpdispatchcallback)
    -   [**WdfDeviceInitSetReleaseHardwareOrderOnFailure**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceinitsetreleasehardwareorderonfailure)
    -   [**WdfDeviceInitSetRemoveLockOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceinitsetremovelockoptions)
    -   [**WdfDeviceWdmDispatchIrp**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicewdmdispatchirp)
    -   [**WdfDmaEnablerConfigureSystemProfile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/nf-wdfdmaenabler-wdfdmaenablerconfiguresystemprofile)
    -   [**WdfDmaTransactionAllocateResources**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionallocateresources)
    -   [**WdfDmaTransactionCancel**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactioncancel)
    -   [**WdfDmaTransactionFreeResources**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionfreeresources)
    -   [**WdfDmaTransactionGetTransferInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactiongettransferinfo)
    -   [**WdfDmaTransactionInitializeUsingOffset**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactioninitializeusingoffset)
    -   [**WdfDmaTransactionSetChannelConfigurationCallback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionsetchannelconfigurationcallback)
    -   [**WdfDmaTransactionSetDeviceAddressOffset**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionsetdeviceaddressoffset)
    -   [**WdfDmaTransactionSetImmediateExecution**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionsetimmediateexecution)
    -   [**WdfDmaTransactionSetTransferCompleteCallback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionsettransfercompletecallback)
    -   [**WdfDmaTransactionWdmGetTransferContext**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nf-wdfdmatransaction-wdfdmatransactionwdmgettransfercontext)
    -   [**WdfInterruptQueueWorkItemForIsr**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nf-wdfinterrupt-wdfinterruptqueueworkitemforisr)
    -   [**WdfInterruptReportActive**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nf-wdfinterrupt-wdfinterruptreportactive)
    -   [**WdfInterruptReportInactive**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nf-wdfinterrupt-wdfinterruptreportinactive)
    -   [**WdfInterruptTryToAcquireLock**](https://msdn.microsoft.com/library/windows/hardware/hh439284)
    -   [**WdfIoQueueStopAndPurge**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopandpurge)
    -   [**WdfIoQueueStopAndPurgeSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfio/nf-wdfio-wdfioqueuestopandpurgesynchronously)
    -   [**WdfIoTargetPurge**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/nf-wdfiotarget-wdfiotargetpurge)
    -   [**WdfUsbTargetDeviceCreateIsochUrb**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdevicecreateisochurb)
    -   [**WdfUsbTargetDeviceCreateUrb**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdevicecreateurb)
    -   [**WdfUsbTargetDeviceCreateWithParameters**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdevicecreatewithparameters)
    -   [**WdfUsbTargetDeviceQueryUsbCapability**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbtargetdevicequeryusbcapability)
-   Added [*EvtDeviceUsageNotificationEx*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_usage_notification_ex).

-   Added **IdleTimeoutType** and **ExcludeD3Cold** members to [**WDF\_DEVICE\_POWER\_POLICY\_IDLE\_SETTINGS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/ns-wdfdevice-_wdf_device_power_policy_idle_settings).

-   Added **ReportInactiveOnPowerDown** member to [**WDF\_INTERRUPT\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/ns-wdfinterrupt-_wdf_interrupt_config).

-   Added **WdfIoTargetPurged** value to [**WDF\_IO\_TARGET\_STATE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfiotarget/ne-wdfiotarget-_wdf_io_target_state).

-   Added **WdfSpecialFileBoot** value to [**WDF\_SPECIAL\_FILE\_TYPE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/ne-wdfdevice-_wdf_special_file_type).

-   Added **DbgWaitForSignalTimeoutInSec** to [Registry Values for Debugging Framework-based Drivers](registry-values-for-debugging-kmdf-drivers.md).

-   Added [InstallWdf](https://go.microsoft.com/fwlink/p/?linkid=256122), [MultiComp](https://go.microsoft.com/fwlink/p/?linkid=256158), and [SingleComp](https://go.microsoft.com/fwlink/p/?linkid=256158) samples.

## KMDF Version 1.9


Version 1.9 adds the following functionality:

-   [Guaranteed forward progress](guaranteeing-forward-progress-of-i-o-operations.md) for I/O queues

-   Support for [requeuing I/O requests](requeuing-i-o-requests.md) from a child device's I/O queue to a parent device's I/O queue

-   Ability to specify [queue-level synchronization](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/ne-wdfobject-_wdf_synchronization_scope) for individual queue objects.

-   The following methods:
    -   [**WdfDeviceGetSystemPowerAction**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdevicegetsystempoweraction)
    -   [**WdfDeviceRemoveDependentUsageDeviceObject**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceremovedependentusagedeviceobject)
    -   [**WdfInterruptSetExtendedPolicy**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nf-wdfinterrupt-wdfinterruptsetextendedpolicy)
    -   [**WdfPdoInitAllowForwardingRequestToParent**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfpdo/nf-wdfpdo-wdfpdoinitallowforwardingrequesttoparent)
    -   [**WdfPdoInitAssignContainerID**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfpdo/nf-wdfpdo-wdfpdoinitassigncontainerid)
    -   [**WdfPreDeviceInstallEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinstaller/nf-wdfinstaller-wdfpredeviceinstallex)
    -   [**WdfRequestForwardToParentDeviceIoQueue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestforwardtoparentdeviceioqueue)
    -   [**WdfRequestMarkCancelableEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestmarkcancelableex)
-   Added the **NumberOfPresentedRequests** member to the [**WDF\_IO\_QUEUE\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfio/ns-wdfio-_wdf_io_queue_config) structure so drivers can limit the number of I/O requests that the framework delivers to the driver from a parallel I/O queue.

-   Added the **WdfFileObjectCanBeOptional** flag to the [**WDF\_FILEOBJECT\_CLASS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/ne-wdfdevice-_wdf_fileobject_class) structure.

-   Added the **TolerableDelay** member to the [**WDF\_TIMER\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdftimer/ns-wdftimer-_wdf_timer_config) structure.

-   Added [WdfDefaultIdleInWorkingState and WdfDefaultWakeFromSleepState](user-control-of-device-idle-and-wake-behavior.md) registry values.

## KMDF Version 1.7


-   The [**WdfDeviceEnqueueRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nf-wdfdevice-wdfdeviceenqueuerequest) method can be called at IRQL&lt;=DISPATCH\_LEVEL.

-   The [**WdfWorkItemEnqueue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfworkitem/nf-wdfworkitem-wdfworkitemenqueue) method can be called if the specified work item is already on the work-item queue.

-   Added the [*EvtDeviceArmWakeFromSxWithReason*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_arm_wake_from_sx_with_reason) event callback function.

-   Added **ArmForWakeIfChildrenAreArmedForWake** and **IndicateChildWakeOnParentWake** members to the [**WDF\_DEVICE\_POWER\_POLICY\_WAKE\_SETTINGS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/ns-wdfdevice-_wdf_device_power_policy_wake_settings) structure.

## KMDF Version 1.5


-   [**WdfUsbInterfaceGetNumSettings**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfusb/nf-wdfusb-wdfusbinterfacegetnumsettings)

-   Added the **DriverPoolTag** member to [**WDF\_DRIVER\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/ns-wdfdriver-_wdf_driver_config).

## KMDF Version 1.1


-   The following methods:
    -   [**WdfCommonBufferCreateWithConfig**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfcommonbuffer/nf-wdfcommonbuffer-wdfcommonbuffercreatewithconfig)
    -   [**WdfDmaEnablerGetFragmentLength**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/nf-wdfdmaenabler-wdfdmaenablergetfragmentlength)
    -   [**WdfDmaEnablerWdmGetDmaAdapter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmaenabler/nf-wdfdmaenabler-wdfdmaenablerwdmgetdmaadapter)

## KMDF Version 1.0


Initial release.

 

 





