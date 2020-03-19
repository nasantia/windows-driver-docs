---
title: Resolving Host Names and IP Addresses
description: Resolving Host Names and IP Addresses
ms.assetid: 4a5f421c-6827-4ca2-be88-67ec43dc84b2
keywords:
- WSK WDK networking , name resolution
- Winsock Kernel WDK networking , name resolution
- host name translation to transport address WDK Winsock Kernel
- transport address translation to host name WDK Winsock Kernel
- transport addresses WDK Winsock Kernel
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Resolving Host Names and IP Addresses


Beginning with Windows 7, a *kernel name resolution* feature allows kernel-mode components to perform protocol-independent translation between Unicode host names and transport addresses. You can use the following [Winsock Kernel (WSK)](https://docs.microsoft.com/windows-hardware/drivers/ddi/_netvista/) client-level functions to perform this name resolution:

-   [**WskFreeAddressInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nc-wsk-pfn_wsk_free_address_info)

-   [**WskGetAddressInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nc-wsk-pfn_wsk_get_address_info)

-   [**WskGetNameInfo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nc-wsk-pfn_wsk_get_name_info)

These functions perform name-address translation similarly to the user-mode functions [**FreeAddrInfoW**](https://docs.microsoft.com/windows/desktop/api/ws2tcpip/nf-ws2tcpip-freeaddrinfow), [**GetAddrInfoW**](https://docs.microsoft.com/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfow), and [**GetNameInfoW**](https://docs.microsoft.com/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getnameinfow), respectively.

To take advantage of this feature, you must compile or recompile your driver with the NTDDI\_VERSION macro set to NTDDI\_WIN7 or greater.

In order for your driver to use kernel name resolution functionality, it must perform the following calling sequence:

1.  Call [**WskRegister**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nf-wsk-wskregister) to register with WSK.

2.  Call [**WskCaptureProviderNPI**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nf-wsk-wskcaptureprovidernpi) to capture the WSK provider [Network Programming Interface (NPI)](network-programming-interface.md).

3.  When you are done using the WSK provider NPI, call [**WskReleaseProviderNPI**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nf-wsk-wskreleaseprovidernpi) to release the WSK provider NPI.

4.  Call [**WskDeregister**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wsk/nf-wsk-wskderegister) to deregister the WSK application.

The following code example uses the above calling sequence to show how a WSK application can call the **WskGetAddressInfo** function to translate a host name to a transport address.

```C++
NTSTATUS
SyncIrpCompletionRoutine(
    __in PDEVICE_OBJECT Reserved,
    __in PIRP Irp,
    __in PVOID Context
    )
{    
    PKEVENT compEvent = (PKEVENT)Context;
    UNREFERENCED_PARAMETER(Reserved);
    UNREFERENCED_PARAMETER(Irp);
    KeSetEvent(compEvent, 2, FALSE);    
    return STATUS_MORE_PROCESSING_REQUIRED;
}

NTSTATUS
KernelNameResolutionSample(
    __in PCWSTR NodeName,
    __in_opt PCWSTR ServiceName,
    __in_opt PADDRINFOEXW Hints,
    __in PWSK_PROVIDER_NPI WskProviderNpi
    )
{
    NTSTATUS status;
    PIRP irp;
    KEVENT completionEvent;
    UNICODE_STRING uniNodeName, uniServiceName, *uniServiceNamePtr;
    PADDRINFOEXW results;

    PAGED_CODE();
    //
    // Initialize UNICODE_STRING structures for NodeName and ServiceName 
    //
 
    RtlInitUnicodeString(&uniNodeName, NodeName);

    if(ServiceName == NULL) {
        uniServiceNamePtr = NULL;
    }
    else {
        RtlInitUnicodeString(&uniServiceName, ServiceName);
        uniServiceNamePtr = &uniServiceName;
    }

    //
    // Use an event object to synchronously wait for the 
    // WskGetAddressInfo request to be completed. 
    //
 
    KeInitializeEvent(&completionEvent, SynchronizationEvent, FALSE);

    //
    // Allocate an IRP for the WskGetAddressInfo request, and set the 
    // IRP completion routine, which will signal the completionEvent
    // when the request is completed.
    //
 
    irp = IoAllocateIrp(1, FALSE);
    if(irp == NULL) {
        return STATUS_INSUFFICIENT_RESOURCES;
    }        

    IoSetCompletionRoutine(irp, SyncIrpCompletionRoutine, 
  &completionEvent, TRUE, TRUE, TRUE);

    //
    // Make the WskGetAddressInfo request.
    //
 
    WskProviderNpi->Dispatch->WskGetAddressInfo (
        WskProviderNpi->Client,
        &uniNodeName,
        uniServiceNamePtr,
        NS_ALL,
        NULL, // Provider
        Hints,
        &results, 
        NULL, // OwningProcess
        NULL, // OwningThread
        irp);

    //
    // Wait for completion. Note that processing of name resolution results
    // can also be handled directly within the IRP completion routine, but
    // for simplicity, this example shows how to wait synchronously for 
    // completion.
    //
 
    KeWaitForSingleObject(&completionEvent, Executive, 
                        KernelMode, FALSE, NULL);

    status = irp->IoStatus.Status;

    IoFreeIrp(irp);

    if(!NT_SUCCESS(status)) {
        return status;
    }

    //
    // Process the name resolution results by iterating through the addresses
    // within the returned ADDRINFOEXW structure.
    //
 
   results; // your code here

    //
    // Release the returned ADDRINFOEXW structure when no longer needed.
    //
 
    WskProviderNpi->Dispatch->WskFreeAddressInfo(
        WskProviderNpi->Client,
        results);

    return status;
} 
```

 

 





