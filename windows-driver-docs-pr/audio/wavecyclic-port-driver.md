---
title: WaveCyclic Port Driver
description: WaveCyclic Port Driver
ms.assetid: c5572ae3-0d91-43a6-a49c-c6c005263f5b
keywords:
- WaveCyclic port driver WDK audio
- PortCls WDK audio , port drivers
- audio miniport drivers WDK , port drivers
- miniport drivers WDK audio , port drivers
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# WaveCyclic Port Driver


## <span id="wavecyclic_port_driver"></span><span id="WAVECYCLIC_PORT_DRIVER"></span>


**Important**  The use of WaveCyclic is no longer recommended, instead use WaverRT.

 

The WaveCyclic port driver manages the playback or recording of a wave stream by a DMA-based audio device that processes audio data in a cyclic buffer. This device is a hardware function on an audio adapter. Typically, the adapter is part of an integrated chipset on the motherboard or is mounted on an audio card that plugs into a PCI or ISA slot on the motherboard. The adapter driver provides a corresponding [WaveCyclic miniport driver](wavecyclic-miniport-driver.md) driver object that binds to the WaveCyclic port driver object to form a [wave filter](wave-filters.md) that can capture or render a wave stream.

The WaveCyclic port driver exposes an [IPortWaveCyclic](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iportwavecyclic) interface to the miniport driver. IPortWaveCyclic inherits the methods in base interface [IPort](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iport). IPortWaveCyclic provides the following additional methods:

[**IPortWaveCyclic::NewMasterDmaChannel**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iportwavecyclic-newmasterdmachannel)

Creates a new master DMA channel object for an audio device with a built-in DMA controller.

[**IPortWaveCyclic::NewSlaveDmaChannel**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iportwavecyclic-newslavedmachannel)

Creates a new subordinate DMA channel object for an audio device without a built-in DMA controller.

[**IPortWaveCyclic::Notify**](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nf-portcls-iportwavecyclic-notify)

Notifies the port driver that the DMA controller has advanced to a new position in the audio stream.

The WaveCyclic port and miniport driver objects communicate with each other through their respective [IPortWaveCyclic](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iportwavecyclic) and [IMiniportWaveCyclic](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iminiportwavecyclic) interfaces. In addition, the port driver communicates with the miniport driver's stream objects through their [IMiniportWaveCyclicStream](https://docs.microsoft.com/windows-hardware/drivers/ddi/portcls/nn-portcls-iminiportwavecyclicstream) interfaces.

 

 




