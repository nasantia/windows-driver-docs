---
title: Audio Helper Object Interfaces
description: Audio Helper Object Interfaces
ms.assetid: 94d3f7f3-7ccc-4f66-b5fa-95f18b8a0f17
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# Audio Helper Object Interfaces


## <span id="ddk_audio_helper_object_interfaces_ks"></span><span id="DDK_AUDIO_HELPER_OBJECT_INTERFACES_KS"></span>


The Port Class Library (portcls.sys) implements a variety of helper objects that provide functionality that is of general use to adapter drivers. These helper objects provide mechanisms for managing DMA channels, interrupt requests, registry access, resource lists, digital rights, and hardware events. This section provides details on the interfaces that are exposed by those objects.

The following interfaces are described in this section:


[IDrmPort](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-idrmport)

Helps a miniport driver keep track of composite DRM rights.

[IDrmPort2](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-idrmport2)

Helps a miniport driver keep track of composite DRM rights. This is an extended version of **IDrmPort**.

[IInterruptSync](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iinterruptsync)

A synchronization mechanism for coordinating shared access to interrupt service requests.

[IMasterClock](https://docs.microsoft.com/windows-hardware/drivers/ddi/dmusicks/nn-dmusicks-imasterclock)

Provides DirectMusic streams with access to the current reference time from the master clock.

[**IPortClsEtwHelper**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iportclsetwhelper)

Used by a miniport driver to access Event Tracing for Windows (ETW) helper functions.
[IPortClsVersion](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iportclsversion)

Identifies the version of the Microsoft Windows operating system that the driver is running on.

[IPortEvents](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iportevents)

Used by a miniport driver to notify a port driver of hardware events.

[IPreFetchOffset](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iprefetchoffset)

Sets the prefetch offset, which is the number of bytes of data separating the write cursor from the play cursor in a Microsoft DirectSound hardware buffer.

[IRegistryKey](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iregistrykey)

Provides read/write access to a registry key and its subkeys.

[IResourceList](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iresourcelist)

Specifies a list of resources such as I/O ports, DMA channels, and interrupts.

[IServiceGroup](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iservicegroup)

Used to demultiplex interrupt service requests to a list of objects with [IServiceSink](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iservicesink) interfaces.

[IServiceSink](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iservicesink)

Represents the target of an interrupt service request.

[IUnregisterPhysicalConnection](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iunregisterphysicalconnection)

Deletes the registration of a physical connection between two subdevices in the same audio adapter or in two different adapters.

[IUnregisterSubdevice](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iunregistersubdevice)

Deletes the registration of a dynamic subdevice in an audio adapter.

 

 





