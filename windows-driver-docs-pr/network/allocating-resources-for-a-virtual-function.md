---
title: Allocating Resources for a Virtual Function
description: Allocating Resources for a Virtual Function
ms.assetid: 00191D2C-E093-4DB7-AC82-8E8E5A74656F
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Allocating Resources for a Virtual Function


A network adapter that supports single root I/O virtualization (SR-IOV) must be able to support the following hardware components:

-   One PCI Express (PCIe) Physical Function (PF). The PF always exists on the network adapter and is attached to the Hyper-V parent partition.

    For more information on this hardware component, see [SR-IOV Physical Function (PF)](sr-iov-physical-function--pf-.md).

-   One or more PCIe Virtual Functions (VF). Each VF must be initialized and attached to a Hyper-V child partition before the networking components of the guest operating system can send or receive packets over the VF.

    For more information on this hardware component, see [SR-IOV Virtual Functions (VFs)](sr-iov-virtual-functions--vfs-.md).

The PF miniport driver, which runs in the management operating system of the Hyper-V parent partition, allocates resources for the PF and each VF on the SR-IOV network adapter. This driver allocates resources for the PF as it would for any network adapter. However, the driver allocates resources for each VF in the following way:

-   The PF miniport driver allocates hardware resources for each VF when the driver creates the network interface card (NIC) on the network adapter. The driver completes the hardware resource allocation for the VFs by calling [**NdisMEnableVirtualization**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismenablevirtualization). For more information on this process, see [Creating a NIC Switch](creating-a-nic-switch.md).

-   The PF miniport driver allocates software resources for a VF when the driver handles an object identifier (OID) method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf). Even though the hardware resources have been allocated for a VF, it is considered nonoperational until the PF miniport driver successfully completes the OID\_NIC\_SWITCH\_ALLOCATE\_VF.

The overlying driver can request the allocation of software resources for a VF by issuing an OID method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf). The **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure for the OID request contains a pointer to an [**NDIS\_NIC\_SWITCH\_VF\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_nic_switch_vf_parameters) structure.

After a successful return from the OID request, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to an [**NDIS\_NIC\_SWITCH\_VF\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_nic_switch_vf_parameters) structure. This structure has an adapter-unique VF identifier and PCI Requestor Identifier (RID). These identifiers are used in the following ways:

-   The overlying driver uses the VF identifier in actions related to the VF, such as the following:

    -   Obtaining the current VF parameters through an OID method request of [OID\_NIC\_SWITCH\_VF\_PARAMETERS](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-vf-parameters).

    -   Freeing previously allocated resources for the VF through an OID set request of [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf).

    -   Issuing a PCI reset to the VF through an OID set request of [OID\_SRIOV\_RESET\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-sriov-reset-vf).

-   The RID is used by the virtualization stack for remapping DMA and interrupts between the PF and VF. The RID also enables the hardware input/output memory management unit (IOMMU) to convert guest physical addresses to host physical addresses.

For more information on how the overlying driver issues [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf) method requests, see [Issuing OID\_NIC\_SWITCH\_ALLOCATE\_VF Requests](issuing-oid-nic-switch-allocate-vf-requests.md).

For more information on how the PF miniport driver handles [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf) method requests, see [Handling OID\_NIC\_SWITCH\_ALLOCATE\_VF Requests](handling-oid-nic-switch-allocate-vf-requests.md).

**Note**  After resources for a VF have been allocated through an OID method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf), the resource parameters for the VF cannot be changed dynamically.

 

 

 





