---
title: Creating the WIA Driver Item Tree
description: Creating the WIA Driver Item Tree
ms.assetid: 3ae489b9-175e-4b1e-a6c8-a72a3a3c212a
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Creating the WIA Driver Item Tree





After the minidriver is initialized, it must create the driver item tree in the [**IWiaMiniDrv::drvInitializeWia**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiaminidrv-drvinitializewia) method by:

1.  Creating the driver item tree if it does not already exist. The minidriver sets the root item flags and creates the root item by calling the driver services library function [**wiasCreateDrvItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamdef/nf-wiamdef-wiascreatedrvitem). The minidriver stores the returned pointer to the root item in a private member variable.

2.  Creating child items for each item on the device using the [**wiasCreateDrvItem**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamdef/nf-wiamdef-wiascreatedrvitem) function. This function creates a device-specific context where the minidriver can store information about the item.

3.  Calling the [**IWiaDrvItem::AddItemToFolder**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamindr_lh/nf-wiamindr_lh-iwiadrvitem-additemtofolder) method on each child item to add the item to the driver item tree.

 

 




