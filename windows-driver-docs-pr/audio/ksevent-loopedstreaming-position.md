---
title: KSEVENT\_LOOPEDSTREAMING\_POSITION
description: The KSEVENT\_LOOPEDSTREAMING\_POSITION event indicates that the audio stream has reached a specified position in a looped buffer.Usage Summary TableTargetEvent Descriptor TypeEvent Value TypePinKSEVENTLOOPEDSTREAMING\_POSITION\_EVENT\_DATA The event value type (operation data) is a LOOPEDSTREAMING\_POSITION\_EVENT\_DATA structure that contains the following information The type of notification that the system will send to the client when the position event occurs.The buffer position that triggers the event.
ms.assetid: 6609ddac-e506-4fab-b580-0def30be2e9c
keywords: ["KSEVENT_LOOPEDSTREAMING_POSITION Audio Devices"]
topic_type:
- apiref
api_name:
- KSEVENT_LOOPEDSTREAMING_POSITION
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
---

# KSEVENT\_LOOPEDSTREAMING\_POSITION


The KSEVENT\_LOOPEDSTREAMING\_POSITION event indicates that the audio stream has reached a specified position in a looped buffer.

**Usage Summary Table**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Target</th>
<th align="left">Event Descriptor Type</th>
<th align="left">Event Value Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Pin</p></td>
<td align="left"><p><a href="https://docs.microsoft.com/previous-versions/ff561744(v=vs.85)" data-raw-source="[&lt;strong&gt;KSEVENT&lt;/strong&gt;](https://docs.microsoft.com/previous-versions/ff561744(v=vs.85))"><strong>KSEVENT</strong></a></p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-loopedstreaming_position_event_data" data-raw-source="[&lt;strong&gt;LOOPEDSTREAMING_POSITION_EVENT_DATA&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-loopedstreaming_position_event_data)"><strong>LOOPEDSTREAMING_POSITION_EVENT_DATA</strong></a></p></td>
</tr>
</tbody>
</table>

 

The event value type (operation data) is a LOOPEDSTREAMING\_POSITION\_EVENT\_DATA structure that contains the following information:

-   The type of notification that the system will send to the client when the position event occurs.

-   The buffer position that triggers the event.

This event is intended only for internal use by the system.

Remarks
-------

In Windows Server 2003, Windows XP, Windows 2000, Windows Me, and Windows 98, the WavePci and WaveCyclic port drivers contain their own built-in handlers for KSEVENT\_LOOPEDSTREAMING\_POSITION events. WavePci and WaveCyclic miniport drivers should not implement handlers for these events.

In Windows Vista, none of the Wave*Xxx* port drivers implement event handlers or other support for KSEVENT\_LOOPEDSTREAMING\_POSITION events.

A looped buffer is a data buffer for an audio stream of type [**KSINTERFACE\_STANDARD\_LOOPED\_STREAMING**](https://docs.microsoft.com/windows-hardware/drivers/stream/ksinterface-standard-looped-streaming). When a play or record cursor reaches the end of a looped buffer, the cursor wraps around to the start of the buffer.

For more information about looped buffers, buffer positions, and play and record cursors, see [Audio Position Property](https://docs.microsoft.com/windows-hardware/drivers/audio/audio-position-property).

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSEVENT**](https://docs.microsoft.com/previous-versions/ff561744(v=vs.85))

[**KSINTERFACE\_STANDARD\_LOOPED\_STREAMING**](https://docs.microsoft.com/windows-hardware/drivers/stream/ksinterface-standard-looped-streaming)

[**LOOPEDSTREAMING\_POSITION\_EVENT\_DATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-loopedstreaming_position_event_data)

 

 






