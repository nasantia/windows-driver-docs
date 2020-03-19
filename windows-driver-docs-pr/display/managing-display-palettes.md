---
title: Managing Display Palettes
description: Managing Display Palettes
ms.assetid: a0ff1a9c-82dc-4317-a0ec-c387027a52ba
keywords:
- display drivers WDK Windows 2000 , palettes
- color lookup tables WDK Windows 2000 display
- palettes WDK Windows 2000 display
- color palettes WDK Windows 2000 display
- color index WDK Windows 2000 display
- settable palettes WDK Windows 2000 display
- indexed palettes WDK Windows 2000 display
- RGB colors WDK Windows 2000 display
ms.date: 10/11/2019
ms.localizationpriority: medium
---

# Managing Display Palettes

If the video hardware supports colors that can be set, it maintains a color lookup table called a *palette*. GDI takes each RGB value and translates it into a device *color index* so that it can be displayed. GDI uses precalculated and cached tables for the translation. These tables are accessible to drivers as the user object [*XLATEOBJ*](https://docs.microsoft.com/windows/win32/api/winddi/ns-winddi-xlateobj). Therefore, every GDI graphics function that takes source colors and moves them to a destination device uses a XLATEOBJ structure to translate the colors. For more information about palettes and how GDI handles them, see [GDI Support for Palettes](gdi-support-for-palettes.md).

If the video hardware supports palettes that can be set, GDI calls the [**DrvSetPalette**](https://docs.microsoft.com/windows/win32/api/winddi/nf-winddi-drvsetpalette) requested by the application. GDI passes the new palette to the display driver, and the driver queries the [PALOBJ](https://docs.microsoft.com/windows/win32/api/winddi/ns-winddi-palobj).

The **DrvSetPalette** function supplies a handle to a *PDEV* to the driver, and requests the driver to realize the palette for that device. The driver should set the hardware palette to match the entries in the given palette as closely as possible.

This entry point is required if the device supports a palette that can be set, and should not be provided otherwise. A display driver specifies that its device has a settable palette by setting the GCAPS\_PALMANAGED bit in the **flGraphicsCaps** field of the [DEVINFO](https://docs.microsoft.com/windows/win32/api/winddi/ns-winddi-devinfo) structure returned in [**DrvEnablePDEV**](https://docs.microsoft.com/windows/desktop/api/winddi/nf-winddi-drvenablepdev).

The service routine [PALOBJ_cGetColors](https://docs.microsoft.com/windows/desktop/api/winddi/nf-winddi-palobj_cgetcolors) is available to display drivers. This function downloads RGB colors from an indexed palette, and should be called from within the implementation of *DrvSetPalette*.
