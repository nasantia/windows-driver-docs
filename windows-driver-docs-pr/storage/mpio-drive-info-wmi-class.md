---
title: MPIO\_DRIVE\_INFO WMI Class
description: MPIO\_DRIVE\_INFO WMI Class
ms.assetid: 4c116157-5f5b-4213-abdd-9128ebbfa341
ms.localizationpriority: medium
ms.date: 10/17/2018
---

# MPIO\_DRIVE\_INFO WMI Class


An MPIO driver uses the MPIO\_DRIVE\_INFO WMI class to identify each MPIO disk on a system that it manages.

```cpp
class MPIO_DRIVE_INFO
{
    //
    // Number of Paths to the real device.
    //
    [WmiDataId(1)] uint32 NumberPaths;

    //
    // The MPIODisk(N).
    //
    [WmiDataId(2), MaxLen(63)] string Name;

    //
    // The real device's serial number.
    //
    [WmiDataId(3), MaxLen(63)] string SerialNumber;

    //
    // Friendly name of the DSM controlling the device.
    //
    [WmiDataId(4), MaxLen(63)] string DsmName;
};
```

When this class definition is compiled by the WMI tool suite, it produces the [**MPIO\_DRIVE\_INFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/mpiowmi/ns-mpiowmi-_mpio_drive_info) data structure. There are no methods associated with this WMI class.

 

 





