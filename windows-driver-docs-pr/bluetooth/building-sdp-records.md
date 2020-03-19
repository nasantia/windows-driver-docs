---
title: Building SDP Records
description: Building SDP Records
ms.assetid: ca3c0483-6193-4683-94bb-15466a8f332e
keywords:
- Bluetooth WDK , SDP server communication
- SDP WDK Bluetooth
- Service Discovery Protocol WDK Bluetooth
- browsing services WDK Bluetooth
- searching services WDK Bluetooth
- services browsing WDK Bluetooth
- advertising services WDK Bluetooth
- services advertising WDK Bluetooth
- SdpCreateNodeTree
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Building SDP Records


Profile drivers that advertise their services can build Service Discovery Protocol (SDP) tree hierarchies from scratch and then convert them to an SDP record stream. A profile driver must first call the [**SdpCreateNodeTree**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodetree) function. The **SdpCreateNodeTree** function returns an allocated and empty [**SDP\_TREE\_ROOT\_NODE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdpnode/ns-sdpnode-_sdp_tree_root_node) structure that the profile driver can populate by using the following functions:

[**SdpAddAttributeToTree**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpaddattributetotree)

[**SdpAppendNodeToContainerNode**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpappendnodetocontainernode)

[**SdpCreateNodeAlternative**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodealternative)

[**SdpCreateNodeBoolean**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeboolean)

[**SdpCreateNodeInt128**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeint128)

[**SdpCreateNodeInt16**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeint16)

[**SdpCreateNodeInt32**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeint32)

[**SdpCreateNodeInt64**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeint64)

[**SdpCreateNodeInt8**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeint8)

[**SdpCreateNodeNil**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodenil)

[**SdpCreateNodeSequence**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodesequence)

[**SdpCreateNodeString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodestring)

[**SdpCreateNodeUInt128**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuint128)

[**SdpCreateNodeUInt16**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuint16)

[**SdpCreateNodeUInt32**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuint32)

[**SdpCreateNodeUInt64**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuint64)

[**SdpCreateNodeUInt8**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuint8)

[**SdpCreateNodeUrl**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeurl)

[**SdpCreateNodeUUID128**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuuid128)

[**SdpCreateNodeUUID16**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuuid16)

[**SdpCreateNodeUUID32**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpcreatenodeuuid32)

After the profile driver finishes building the tree-based SDP record, it calls the [**SdpConvertTreeToStream**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthsdpddi/nc-bthsdpddi-pconverttreetostream) function to produce a raw byte stream version of the SDP record. In this form, the SDP record is ready for the profile driver to publish it to the local SDP server. This process can be more convenient for profile drivers to use than constructing an SDP record as a stream.

The **SdpConvertTreeToStream** function allocates the necessary memory to store the stream version of the SDP record. When the profile driver no longer requires an SDP record, it must free the memory using [**ExFreePool**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-exfreepool).

Additionally, when a profile driver no longer requires the tree-based version of an SDP record, it must call [**SdpFreeTree**](https://docs.microsoft.com/windows-hardware/drivers/ddi/sdplib/nf-sdplib-sdpfreetree) to free the memory allocated with the associated SDP\_TREE\_ROOT\_NODE structure.

Profile drivers can obtain a pointer to all of the functions discussed in this topic by querying for the [**BTHDDI\_SDP\_PARSE\_INTERFACE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthsdpddi/ns-bthsdpddi-_bthddi_sdp_parse_interface) and [**BTHDDI\_SDP\_NODE\_INTERFACE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/bthsdpddi/ns-bthsdpddi-_bthddi_sdp_node_interface) interfaces. For more information about how to query for these interfaces, see [Querying for Bluetooth Interfaces](querying-for-bluetooth-interfaces.md).

 

 





