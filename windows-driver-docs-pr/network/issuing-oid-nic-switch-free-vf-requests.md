---
title: Issuing OID_NIC_SWITCH_FREE_VF Requests
description: Issuing OID_NIC_SWITCH_FREE_VF Requests
ms.assetid: D9A8548C-02D8-4537-9053-6B262004CBC4
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Issuing OID\_NIC\_SWITCH\_FREE\_VF Requests


An overlying driver issues an object identifier (OID) set request of [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf) to free resources for a PCI Express (PCIe) Virtual Function (VF). These resources were previously allocated through an OID method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf).

The overlying driver issues the [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf) set request to the miniport driver for the PCIe Physical Function (PF). Before it issues this OID request, the overlying driver must do the following:

1.  The overlying driver must make sure that the VF is not attached to any virtual port (VPort) on the NIC switch of the network adapter. The overlying driver must issue OID set requests of [OID\_NIC\_SWITCH\_DELETE\_VPORT](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-delete-vport) to delete all VPorts that are attached to the VF. For more information, see [Deleting a Virtual Port](deleting-a-virtual-port.md).

2.  The overlying driver initializes an [**NDIS\_NIC\_SWITCH\_FREE\_VF\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_nic_switch_free_vf_parameters) structure. The driver must set the **VFId** member to the VF identifier that was returned in the OID method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf).

The overlying driver issues the OID set request of [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf) by following these steps:

1.  The overlying driver initializes an [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request) structure for the OID method request. The driver sets the **InformationBuffer** member to a pointer to an initialized [**NDIS\_NIC\_SWITCH\_FREE\_VF\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_nic_switch_free_vf_parameters) structure.

2.  The overlying driver calls [**NdisOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisoidrequest) to issue the OID request to the underlying PF miniport driver.

After an overlying driver requests resource allocation for a VF, that driver is the only component that can request the freeing of the resources for the same VF. The overlying driver must issue an OID set request of [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf) to free the VF resources. Before the overlying driver can be halted, it must free the resources for each VF that was allocated by the driver's [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf) request.

**Note**   If an overlying driver issues an OID method request of [OID\_NIC\_SWITCH\_ALLOCATE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-allocate-vf) to allocate resources for a VF, that driver is the only component that can request the freeing of the resources for the same VF. The overlying driver must issue an OID set request of [OID\_NIC\_SWITCH\_FREE\_VF](https://docs.microsoft.com/windows-hardware/drivers/network/oid-nic-switch-free-vf) to free the VF resources. Before the overlying driver can be halted, it must free the resources for each VF that was allocated by the driver's OID\_NIC\_SWITCH\_ALLOCATE\_VF request.

 

 

 





