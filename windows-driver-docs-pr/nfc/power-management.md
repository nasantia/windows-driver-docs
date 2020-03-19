---
title: NFP power management
description: NFP power management
ms.assetid: A47F4B01-A912-410A-8CF8-656D2C125148
keywords:
- NFC
- near field communications
- proximity
- near field proximity
- NFP
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# NFP power management


NFP devices operate in one of three power modes. These modes are *active*, *idle*, *standby*, and *power-removed*. The NFP device can enter a low-power mode when publications or subscriptions to the device are disabled. The NFP driver will transition the device to one of the power modes in response to an enable or disable notification from Windows.

The NFP driver will receive an [**IOCTL\_NFP\_ENABLE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/nfpdev/ni-nfpdev-ioctl_nfp_enable) or an [**IOCTL\_NFP\_DISABLE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/nfpdev/ni-nfpdev-ioctl_nfp_disable) control code to enable or disable subscriptions, publications, and presence events. These control codes will also trigger a power mode change for the device. The [Near-field proximity (NFP) power management for connected standby platforms](https://docs.microsoft.com/windows-hardware/design/device-experiences/near-field-promiximity--nfp--power-management-for-modern-standby-platforms) topic provides detailed description of power mode changes for NFP devices.

 

 
## Related topics
[NFC device driver interface (DDI) overview](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)  
[Near field proximity DDI reference](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)  

