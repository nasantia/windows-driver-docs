---
title: Pairing a driver with a Universal Windows Platform (UWP) app
description: This topic describes how to specify that a Universal Windows Platform (UWP) app should only load if a specific driver is present.
ms.assetid: 50f981bb-e17b-4454-88f9-46b09eb05509
ms.date: 08/24/2017
ms.localizationpriority: medium
---

# Pairing a driver with a Universal Windows Platform (UWP) app

Starting in Windows 10 version 1709, you can specify that a Universal Windows Platform (UWP) app should only load if a specific driver is present. When you use this option, the Microsoft Store offers each user the most recent version of the app that works with the installed version of the driver on that user's computer.

The app can further constrain loading to a particular driver version or date.  This topic describes the steps required in both the app and driver to create such a requirement.

## Steps in the app

To cause a UWP app to load only when a specific driver is present, add two XML elements to the manifest XML (.appx) file for the app:

* [uap5:DriverDependency](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-driverdependency)
* [uap5:DriverConstraint](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-driverconstraint)

In particular, use these elements to specify at least one driver dependency containing at least one driver constraint.  See further details on use of these elements on the reference pages linked to above.  The latter page contains an example.

## Steps in the driver

Next, do the following in the driver's INF file:

1. Specify the [INF AddSoftware Directive](inf-addsoftware-directive.md).
2. Set the **SoftwareType** entry to 2.
3. Provide a Package Family Name (PFN) in the **SoftwareID** entry.

In addition to matching the most recent app and driver versions, the system also tries to match previous app and driver versions.  For example, if app version 2 specifies minimum driver version 2, and app version 1 specifies minimum driver version 1, a system that has driver version 1 will successfully load app version 1.

## See Also

* [uap5:DriverDependency](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-driverdependency)
* [uap5:DriverConstraint](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-driverconstraint)
* [INF AddSoftware Directive](inf-addsoftware-directive.md)
* [Hardware Support App (HSA): Steps for Driver Developers](../devapps/hardware-support-app--hsa--steps-for-driver-developers.md)
* [Hardware Support App (HSA): Steps for App Developers](../devapps/hardware-support-app--hsa--steps-for-app-developers.md)
