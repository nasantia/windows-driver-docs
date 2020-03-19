---
title: NetAdapterCx receive side scaling (RSS)
description: NetAdapterCx receive side scaling (RSS)
ms.assetid: 85A819E2-6352-4DE9-9689-3DCEB9B0AAD8
keywords:
- WDF Network Adapter Class Extension Receive Side Scaling, NetAdapterCx receive side scaling, NetAdapterCx RSS, NetAdapter RSS
ms.date: 07/13/2018
ms.localizationpriority: medium
---

# NetAdapterCx receive side scaling (RSS)

Receive side scaling (RSS) is a network driver technology that enables the efficient distribution of network receive processing across multiple CPUs in multiprocessor systems. RSS improves system performance and increases network scalability by harnessing all available processors in a system and dynamically rebalancing CPU workloads. 

This topic highlights RSS for NetAdapterCx client drivers and assumes knowledge of RSS concepts and terminology. For more information about RSS in general, including diagrams illustrating RSS in different hardware scenarios, see [Receive Side Scaling](https://docs.microsoft.com/windows-hardware/drivers/network/ndis-receive-side-scaling2).

## Overview of RSS in NetAdapterCx

RSS in NetAdapterCx focuses on ease of configuration, simplicity of enablement and disablement, and abstraction of processor-to-interrupt complexity. A client driver for an RSS-capable NIC only needs to meet three criteria to support RSS in NetAdapterCx:

1. The driver must set RSS capabilities when starting a net adapter, but before calling [**NetAdapterStart**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netadapter/nf-netadapter-netadapterstart). This includes implementing four RSS callbacks and registering them in the RSS capabilities structure.
2. The driver's datapath queues must be created and ready to accept requests.
3. The driver must be in the *D0* power state.

The design of RSS in NetAdapterCx guarantees that the system will not call a client's RSS callbacks and enable RSS until the very end of the [power-up sequence](power-up-sequence-for-a-netadaptercx-client-driver.md). Clients do not have to manage indirection table move requests or handle other RSS events until everything they need is ready. 

Later, when the driver is unloading, NetAdapterCx will not call RSS callbacks after datapath queues have been destroyed during the [power-down sequence](power-down-sequence-for-a-netadaptercx-client-driver.md). Since datapath queues are torn down as the first step during power-down, this means that clients do not have to handle possible RSS events at any other stage during power-down.

## Setting RSS capabilities

To get started with RSS in NetAdapterCx, follow these steps:

1. When starting your net adapter, tell the system about your hardware's RSS capabilities and constraints using the [NET_ADAPTER_RECEIVE_SCALING_CAPABILITIES](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/ns-netreceivescaling-_net_adapter_receive_scaling_capabilities) structure.
2. Initialize the capabilities structure by calling [NET_ADAPTER_RECEIVE_SCALING_CAPABILITIES_INIT](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nf-netreceivescaling-net_adapter_receive_scaling_capabilities_init). 
3. When you initialize the RSS capabilities structure, set the structure's RSS callback members to register your implementations for these callbacks:
    1. *[EvtNetAdapterReceiveScalingEnable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_enable)*
    2. *[EvtNetAdapterReceiveScalingDisable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_disable)*
    3. *[EvtNetAdapterReceiveScalingSetHashSecretKey](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_hash_secret_key)*
    4. *[EvtNetAdapterReceiveScalingSetIndirectionEntries](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_indirection_entries)*
4. Set the RSS capabilities structure's **SynchronizeSetIndirectionEntries** as appropriate.
5. Pass the initialized RSS capabilities structures to the [NetAdapterSetReceiveScalingCapabilities](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nf-netreceivescaling-netadaptersetreceivescalingcapabilities) method.

## Enabling and disabling RSS

After you set RSS capabilities, the system will continue with the power-up sequence for your driver. NetAdapterCx starts invoking your driver's RSS callbacks once the final step of creating datapath queues has finished. At this point, RSS can be enabled and disabled as needed by the system. 

> [!IMPORTANT]
> You should **not** clear or reset your indirection table when enabling or disabling RSS. The framework will set the your initial indirection table state.

### Enabling RSS

NetAdapterCx enables RSS by invoking your driver's *[EvtNetAdapterReceiveScalingEnable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_enable)* callback. In the context of this callback, you typically enable control bits in your hardware. 

For a code example of enabling RSS, see *[EvtNetAdapterReceiveScalingEnable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_enable)*.

### Disabling RSS

NetAdapterCx disables RSS by invoking your driver's *[EvtNetAdapterReceiveScalingDisable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_disable)* callback. Here, you typically disable the control bit in your hardware that you previously set in *EvtNetAdapterReceiveScalingEnable*. 

For a code example of disabling RSS, see *[EvtNetAdapterReceiveScalingDisable](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_disable)*.

## Setting the hash secret key

Once RSS is enabled, NetAdapterCx invokes the *[EvtNetAdapterReceiveScalingSetHashSecretKey](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_hash_secret_key)* callback to provide your driver with the hash secret key your NIC should use in verifying hash calculations. This callback can be invoked at any time when RSS is running if the hash secret key changes. 

For a code example of setting the hash secret key, see *[EvtNetAdapterReceiveScalingSetHashSecretKey](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_hash_secret_key)*.

## Moving indirection table entries

While RSS is running on the system, upper layer protocol drivers monitor processor workload and maintain an indirection table that maps receive queues to processors. When the protocol driver needs to rebalance processor workload in RSS, it first calculates a new mapping for each indirection table entry to a new processor. Then the protocol passes this information to NetAdapterCx, which handles the complexity of mapping receive queues and hardware interrupt vectors to the correct processor on behalf of your NIC client driver. NetAdapterCx stores the new indirection table, with entries mapped to receive queue IDs, in a [NET_ADAPTER_RECEIVE_SCALING_INDIRECTION_ENTRIES](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/ns-netreceivescaling-_net_adapter_receive_scaling_indirection_entries) structure and passes it to your driver when it invokes the *[EvtNetAdapterReceiveScalingSetIndirectionEntries](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_indirection_entries)* callback function. 

In this callback, you move each entry in your NIC's indirection table to the specified receive queue. Each [NET_ADAPTER_RECEIVE_SCALING_INDIRECTION_ENTRY](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/ns-netreceivescaling-_net_adapter_receive_scaling_indirection_entry) structure in the **NET_ADAPTER_RECEIVE_SCALING_INDIRECTION_ENTRIES** array contains the hash index for that entry in the table, the new receive queue to which to assign the entry, and a status field indicating if that individual move succeeded or not. 

The method of assigning index entries to hardware receive queues depends on the design of your NIC and the number of receive queues it has. For more information and a code example, see *[EvtNetAdapterReceiveScalingSetIndirectionEntries](https://docs.microsoft.com/windows-hardware/drivers/ddi/netreceivescaling/nc-netreceivescaling-evt_net_adapter_receive_scaling_set_indirection_entries)*.
