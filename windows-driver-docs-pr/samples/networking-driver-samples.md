---
title: Networking driver samples
description: The driver samples in this directory provide a starting point for writing a custom network driver for your device.
ms.assetid: 97C88E82-96AA-41AD-9B1F-3EB848A08BD8
ms.date: 12/02/2019
ms.localizationpriority: medium
---

# Networking driver samples

The driver samples in this directory provide a starting point for writing a custom network driver for your device.

| Sample | Description |
| --- | --- |
| [Bindview](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/bindview-network-configuration-utility) | An application that demonstrates how to use INetCfg APIs to enumerate, install, uninstall, bind and unbind network components. |
| [Fakemodem](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/fakemodem-driver) | Demonstrates a simple controller-less modem driver. |
| [Hyper-V Extensible Switch Extension Filter](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/hyper-v-extensible-switch-extension-filter-driver) | A base library used to implement a Hyper-V Extensible Switch extension filter driver. |
| [NDIS 6.0 Filter](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/ndis-60-filter-driver) | The sample is a do-nothing pass-through NDIS 6 filter driver demonstrating the basic principles of an NDIS 6.0 Filter driver. |
| [NDIS MUX Intermediate Driver and Notify Object](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/ndis-mux-intermediate-driver-and-notify-object) | An NDIS 6.0 driver that demonstrates the operation of an “N:1” MUX driver. The sample create multiple virtual network devices on top of a single lower adapter. |
| [Connectionless NDIS 6.0 and 6.3 Protocol Driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/ndis-connection-less-protocol-wdm-driver-sample) | This driver supports sending and receiving raw Ethernet frames using ReadFile/WriteFile calls from user-mode. As an NDIS protocol driver, it illustrates how to establish and tear down bindings to Ethernet adapters. |
| [Connectionless NDIS 6.0 Protocol Driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/connection-less-ndis-60-protocol-kmdf-sample-driver)| This driver supports sending and receiving raw Ethernet frames using ReadFile/WriteFile calls from user-mode. As an NDIS protocol driver, it illustrates how to establish and tear down bindings to Ethernet adapters. |
| [NDIS Virtual Miniport Driver](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/ndis-virtual-miniport-driver) | Demonstrates the functionality of an NDIS miniport driver without requiring a physical network adapter. |
| [Radio Switch Test Driver for OSR USB-FX2 Development Board](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/radio-switch-test-driver-for-osr-usb-fx2-development-board) | Demonstrates how to structure a HID driver for radio switches for the OSR USB-FX2 Development Board. |
| [Radio Manager](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-radio-management-sample) | Demonstrates how to structure a Radio Manager for use with the Windows Radio Management APIs. |
| [WDI Sample](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wdi-samples) | This sample demonstrates use of the WLAN WDI. |
| [WFP Packet Modification](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-filtering-platform-packet-modification-sample) | Demonstrates the packet modification capabilities of the Windows Filtering Platform (WFP). |
| [WFP Traffic Inspection](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-filtering-platform-traffic-inspection-sample) | Demonstrates the traffic inspection capabilities of the Windows Filtering Platform (WFP).  |
| [WFP MSN Messenger Monitor](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-filtering-platform-msn-messenger-monitor-sample) | A sample application and driver demonstrating the stream inspection capabilities of the Windows Filtering Platform (WFP). |
| [WFP Stream Edit](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-filtering-platform-stream-edit-sample) | Demonstrates replacing a string pattern for a Transmission Control Protocol (TCP) connection using the Windows Filtering Platform (WFP). |
| [Windows Filtering Platform](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/windows-filtering-platform-sample) | This is a sample firewall. It has a command-line interface which allows adding filters at various WFP layers under various conditions. Additionally, it exposes callouts for injection, basic action, proxying, and stream inspection. |
| [Native Wi-Fi IHV Service](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/ihv-sample-ui) | Demonstrates IHV extensibility for native Wi-Fi. |
| [WSK TCP Echo Server](https://docs.microsoft.com/samples/microsoft/windows-driver-samples/wsk-tcp-echo-server) | This sample driver is a minimal driver meant to demonstrate the usage of the Winsock Kernel (WSK) programming interface. |
