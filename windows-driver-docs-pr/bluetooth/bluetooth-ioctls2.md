---
title: Bluetooth IOCTLs
description: Bluetooth IOCTLs
ms.assetid: 384ea4bb-863c-4da7-bf81-85d2de734ef7
keywords:
- Bluetooth WDK , IOCTLs
- IOCTLs WDK Bluetooth
- local Bluetooth WDK
- remote Bluetooth WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Bluetooth IOCTLs


The Bluetooth driver stack provides profile drivers with several IOCTLs to gather information about:

-   The local Bluetooth radio and system.

-   Remote Bluetooth devices.

-   The device that caused the Plug and Play (PnP) Manager to load a profile driver.

To gather information about the local Bluetooth radio and system, a profile driver uses [**IOCTL\_BTH\_GET\_LOCAL\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ni-bthioctl-ioctl_bth_get_local_info). After the IOCTL returns, its **AssociatedIrp.SystemBuffer** member contains a pointer to a [**BTH\_LOCAL\_RADIO\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ns-bthioctl-_bth_local_radio_info) structure that contains information about the local Bluetooth radio and system, including flags that indicate whether the local radio can be discovered and connected to. The returned BTH\_LOCAL\_RADIO\_INFO structure contains a [BTH\_DEVICE\_INFO](https://go.microsoft.com/fwlink/p/?linkid=50713) structure, which contains system-specific information, and a [**BTH\_RADIO\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ns-bthioctl-_bth_radio_info) structure, which contains local radio-specific information.

To gather information about a specific remote Bluetooth device, a profile driver uses [**IOCTL\_BTH\_GET\_RADIO\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ni-bthioctl-ioctl_bth_get_radio_info). After the IOCTL returns, its **AssociatedIrp.SystemBuffer** member contains a pointer to a BTH\_RADIO\_INFO structure that provides information about the specific remote radio, including whether the remote radio can be discovered and connected to.

To gather information about all remote radios that have been discovered, a profile driver uses [**IOCTL\_BTH\_GET\_DEVICE\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ni-bthioctl-ioctl_bth_get_device_info). After the IOCTL returns, its **AssociatedIrp.SystemBuffer** member contains a pointer to a [**BTH\_DEVICE\_INFO\_LIST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ns-bthioctl-_bth_device_info_list) structure that contains an array of BTH\_DEVICE\_INFO structures. The BTH\_DEVICE\_INFO\_LIST structure contains one array entry for each discovered remote radio. The user-mode [BluetoothGetDeviceInfo](https://go.microsoft.com/fwlink/p/?linkid=74493) API uses this functionality to return information about all remote radios.

To gather information about the remote device that caused the PnP Manager to load it, a profile driver uses [**IOCTL\_INTERNAL\_BTHENUM\_GET\_DEVINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ni-bthioctl-ioctl_internal_bthenum_get_devinfo). After the IOCTL returns, its **AssociatedIrp.SystemBuffer** member contains a pointer to a BTH\_DEVICE\_INFO structure that contains information about the remote device, including its Bluetooth device address, device state, and its class-of-device (CoD) settings.

A profile driver uses [**IOCTL\_INTERNAL\_BTHENUM\_GET\_ENUMINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthioctl/ni-bthioctl-ioctl_internal_bthenum_get_enuminfo) to obtain information about the underlying device and service that caused the PnP manager to load the profile driver. After the IOCTL returns, its **AssociatedIrp.SystemBuffer** member contains a pointer to a [**BTH\_ENUMERATOR\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthddi/ns-bthddi-_bth_enumerator_info) structure that contains vendor-provided information about the device, including the port number, device flags, vendor ID, and product ID.

For more information about using Bluetooth IOCTLs and BRBs, see [Building and Sending a BRB](building-and-sending-a-brb.md).

 

 





