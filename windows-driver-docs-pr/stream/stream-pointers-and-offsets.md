---
title: Stream Pointers and Offsets
description: Stream Pointers and Offsets
ms.assetid: ef9dc015-f0ee-49a6-8774-cfb0223c8b12
keywords:
- stream pointers WDK AVStream , offsets
- offsets WDK AVStream
- stream positions WDK AVStream
- input positions WDK AVStream
- output positions WDK AVStream
- AVStream pointers WDK
- AVStream offsets WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Stream Pointers and Offsets





A [**KSSTREAM\_POINTER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksstream_pointer) structure contains two [**KSSTREAM\_POINTER\_OFFSET**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksstream_pointer_offset) structures that index input and output positions within a frame. A minidriver can either manipulate these offsets or access the data at frame resolution.

To advance a stream pointer within a frame, the minidriver calls [**KsStreamPointerAdvanceOffsets**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nf-ks-ksstreampointeradvanceoffsets) and [**KsStreamPointerAdvanceOffsetsAndUnlock**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nf-ks-ksstreampointeradvanceoffsetsandunlock).

Minidrivers that access stream data with virtual addresses can use these offsets to specify a stream position at byte resolution. Minidrivers that use scatter/gather physical mappings can specify stream position at the granularity of a [**KSMAPPING**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksmapping) structure.

 

 




