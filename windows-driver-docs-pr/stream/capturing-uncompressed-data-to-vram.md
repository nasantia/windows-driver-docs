---
title: Capturing Uncompressed Data to VRAM
description: Capturing Uncompressed Data to VRAM
ms.assetid: efec607d-3337-40a5-812c-57292f201d54
keywords:
- VRAM capture WDK AVStream , uncompressed data
- uncompressed data WDK VRAM capture
- formats WDK VRAM capture
- pin VRAM processing WDK AVStream
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Capturing Uncompressed Data to VRAM


AVStream minidrivers that are VRAM-enabled can capture uncompressed data by providing the following support in the capture pin descriptor.

-   In the corresponding [**KSPIN\_DESCRIPTOR**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kspin_descriptor) structure, list the formats that the capture pin supports in the **DataRanges** member, an array of [**KSDATARANGE**](https://docs.microsoft.com/previous-versions/ff561658(v=vs.85)) structures. Provide pointers to KS\_DATARANGE\_VIDEO structures, cast as pointers to KSDATARANGE.

-   In the **VideoInfoHeader** member of each [**KS\_DATARANGE\_VIDEO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_datarange_video) structure, provide a [**KS\_VIDEOINFOHEADER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_videoinfoheader) structure. Each KS\_VIDEOINFOHEADER contains a [**KS\_BITMAPINFOHEADER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-tagks_bitmapinfoheader).

-   To expose binary formats for MPEG2 capture, set **biCompression** equal to D3DDDIFMT\_BINARYBUFFER, **biHeight** equal to one, and **biWidth** equal to the size of the binary buffer.

The *Capture.cpp* file of the [AVStream Simulated Hardware Sample Driver (AVSHwS)](https://go.microsoft.com/fwlink/p/?linkid=256083) contains examples of the items in the preceding list.

 

 




