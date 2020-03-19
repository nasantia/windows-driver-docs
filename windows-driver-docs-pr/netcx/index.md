---
title: Network Adapter WDF Class Extension (NetAdapterCx)
description: Network Adapter WDF Class Extension (NetAdapterCx)
ms.assetid: 74719A80-AE66-410F-85B7-31B6F455A818
keywords:
- Network Adapter Class Extension, Network Adapter WDF Class Extension, NetAdapterCx, NetCx
ms.date: 08/27/2019
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.custom: 19H1
---

# Network Adapter WDF Class Extension (NetAdapterCx)

## Overview

Starting in Windows 10, version 2004, the Windows Driver Kit (WDK) includes a Network Adapter WDF Class Extension module (NetAdapterCx) that enables you to write a KMDF-based client driver for a Network Interface Controller (NIC). NetAdapterCx gives you the power and flexibility of WDF and the networking performance of NDIS, and makes it easy to write a driver for your NIC.

In previous versions of Windows, WDF and NDIS had individual advantages, but did not interoperate well. The only way to write a NIC driver was to write an NDIS miniport driver. To use WDF in an NDIS miniport driver, you had to write extra code in your driver, and even then, you only had access to a small subset of WDF functionality.

With the NetAdapterCx model, conversely, you write a real WDF driver for your NIC. This means that your NetAdapterCx driver has access to full WDF functionality, as well as networking-specific APIs and I/O support from the NetAdapter class extension. As shown in the block diagram below, NetAdapterCx still works behind the scenes with NDIS, but it handles all the interaction with NDIS on your behalf.

<img src="images/architecture.png" alt="NetAdapterCx architecture" title="NetAdapterCx architecture" width="600"/>

## Additional info

To watch a video that discusses the benefits of using NetAdapterCx, see the [Network Adapter Class Extension: Overview](https://aka.ms/netadapter/video1) video on Channel 9.

To learn how to port an NDIS 6.x miniport driver to the NetAdapterCx NIC driver model, see [Porting NDIS miniport drivers to NetAdapterCx](porting-ndis-miniport-drivers-to-netadaptercx.md).

To start working right away with driver samples on GitHub, clone our [NetAdapter-Cx-Driver-Samples](https://github.com/Microsoft/NetAdapter-Cx-Driver-Samples) repo.

To see the source code for NetAdapterCx itself, or perform step-through debugging, see our [Network-Adapter-Class-Extension](https://github.com/Microsoft/Network-Adapter-Class-Extension) repo on GitHub.

If you would like to work with Microsoft as you develop a NetAdapterCx client driver, or have feedback on the class extension, please send us an [email](mailto:netadapter@microsoft.com).

To watch a video that discusses the future roadmap and collaboration opportunities, see the [Network Adapter Class Extension: Roadmap and Collaboration](https://aka.ms/netadapter/video4) video on Channel 9.

## Topics

This section contains the following topics:

* [Porting NDIS miniport drivers to NetAdapterCx](porting-ndis-miniport-drivers-to-netadaptercx.md)
* [Building a NetAdapterCx client driver](building-a-netadaptercx-client-driver.md)
* [INF files for NetAdapterCx client drivers](inf-files-for-netadaptercx-client-drivers.md)
* [Managing the lifetime of objects in NetAdapterCx](managing-the-lifetime-of-objects-in-netadaptercx.md)
* [Accessing configuration information](accessing-configuration-information.md)
* [Handling control requests](handling-control-requests.md)
* [Debugging a NetAdapterCx client driver](debugging-a-netadaptercx-client-driver.md)
* [Transferring network data](transferring-network-data.md)
* [NetAdapterCx receive side scaling (RSS)](netadaptercx-receive-side-scaling-rss-.md)
* [Configuring power management](configuring-power-management.md)
* [NDIS-WDF function equivalents](ndis-wdf-function-equivalents.md)
* [NetAdapterCx limitations](netadaptercx-limitations.md)
* [Mobile Broadband (MBB) WDF class extension (MBBCx)](mobile-broadband-mbb-wdf-class-extension-mbbcx.md)
