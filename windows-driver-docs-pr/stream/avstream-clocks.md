---
title: AVStream Clocks
description: AVStream Clocks
ms.assetid: fc1d5bca-72e3-48e2-b46f-09a13bba83b4
keywords:
- clocks WDK AVStream
- AVStream clocks WDK
- pin clocks WDK AVStream
- timers WDK AVStream
- time WDK AVStream
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# AVStream Clocks





AVStream filters support clocks on pins.

To indicate that an AVStream pin exposes a clock, set KSPIN\_FLAG\_IMPLEMENT\_CLOCK in the **Flags** member of the first [**KSPIN\_DESCRIPTOR\_EX**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_kspin_descriptor_ex) in the **PinDescriptors** member of [**KSFILTER\_DESCRIPTOR**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksfilter_descriptor).

Also provide a pointer to a [**KSCLOCK\_DISPATCH**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksclock_dispatch) structure in [**KSPIN\_DISPATCH**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_kspin_dispatch).

To make clock requests, use the methods defined on the [IKsReferenceClock](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nn-ks-iksreferenceclock) interface. You can acquire an *IKsReferenceClock* interface by calling [**KsPinGetReferenceClockInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nf-ks-kspingetreferenceclockinterface). The AVStream minidriver is responsible for releasing the interface when finished.

To obtain timer values to place in the **PresentationTime** field of [**KSSTREAM\_HEADER**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksstream_header), call [**IKsReferenceClock::GetCorrelatedTime**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nf-ks-iksreferenceclock-getcorrelatedtime).

Note that the clock never appears in GraphEdit, even if the clock has been selected.

To verify that the clock has been selected, verify that calls to [IKsReferenceClock](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/nn-ks-iksreferenceclock) methods generate calls to dispatch routines specified in KSCLOCK\_DISPATCH.

The filter graph manager selects a clock when a graph transitions into the pause state. Any filter that is a push source, for instance a capture filter, is given preference as a clock provider.

 

 




