---
title: Deinterlace DDI
description: Deinterlace DDI
ms.assetid: 06b85f76-950a-4a9b-af6b-ded823bfda6a
ms.date: 01/05/2018
ms.localizationpriority: medium
---

# Deinterlace DDI


## <span id="ddk_deinterlace_ddi_gg"></span><span id="DDK_DEINTERLACE_DDI_GG"></span>


So that the Video Mixing Renderer (VMR) can deinterlace and perform frame-rate conversion on video content, the display driver must implement the [motion compensation callback functions](https://docs.microsoft.com/windows-hardware/drivers/ddi/index).

To simplify driver development, use motion-compensation code templates and implement the deinterlacing functions in this section. The functions are member functions of either the deinterlace container device or the deinterlace mode device classes. For more information, see [Defining the Deinterlace Container Device Class](https://docs.microsoft.com/windows-hardware/drivers/display/defining-the-deinterlace-container-device-class) and [Defining the Deinterlace Bob Device Class](https://docs.microsoft.com/windows-hardware/drivers/display/defining-the-deinterlace-bob-device-class).

 

 





