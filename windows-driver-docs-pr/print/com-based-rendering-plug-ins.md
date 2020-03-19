---
title: COM-Based Rendering Plug-Ins
description: COM-Based Rendering Plug-Ins
ms.assetid: c80d6c2b-ba4d-4bd1-bd3a-8c1b0bf29884
keywords:
- COM-based rendering plug-ins WDK print
- rendering plug-ins WDK print , COM-based
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# COM-Based Rendering Plug-Ins





To provide customized hooking functions, your COM-based rendering plug-in must implement the [**IPrintOemUni::EnableDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemuni-enabledriver) or [**IPrintOemPS::EnableDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps-enabledriver) method, which fills in a [**DRVENABLEDATA**](https://docs.microsoft.com/windows/desktop/api/winddi/ns-winddi-tagdrvenabledata) structure with the address of each hooking function.

A COM-based rendering plug-in can hook out a graphics DDI function only if the Unidrv or Pscript5 driver defines the function. For a list of such functions, see [**IPrintOemUni::EnableDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemuni-enabledriver) or [**IPrintOemPS::EnableDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps-enabledriver).

If you provide a particular customized hooking function, that function preempts the driver's equivalent graphics DDI function. When you design a customized hooking function, you have the following options:

-   The hooking function can completely handle the graphics DDI operation internally.

-   The hooking function can call back to the printer driver's equivalent graphics DDI function.

By calling back to the driver's graphics DDI function, the hooking function can perform preprocessing or postprocessing of function arguments, but still allow the driver to actually perform the graphics DDI operation. One of the input arguments to a rendering plug-in's [**IPrintOemUni::EnablePDEV**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemuni-enablepdev) or [**IPrintOemPS::EnablePDEV**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps-enablepdev) method is a [**DRVENABLEDATA**](https://docs.microsoft.com/windows/desktop/api/winddi/ns-winddi-tagdrvenabledata) structure that contains pointers to the driver's graphics DDI functions. If you want to call back to these functions, you should save the contents of this structure.

It might be necessary for you to provide a [customized PDEV structure](customized-pdev-structures.md). You can reference this structure from within a graphics DDI hooking function, through the [**SURFOBJ**](https://docs.microsoft.com/windows/desktop/api/winddi/ns-winddi-_surfobj) structure pointer that each hooking function receives as input. Specifically, the SURFOBJ structure's **dhpdev** member points to a [**DEVOBJ**](https://docs.microsoft.com/windows-hardware/drivers/ddi/printoem/ns-printoem-_devobj) structure, and the DEVOBJ structure's **pdevOEM** member points to your customized PDEV structure.

 

 




