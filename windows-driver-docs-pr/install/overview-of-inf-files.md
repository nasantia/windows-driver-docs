---
title: Overview of INF Files
description: Overview of INF Files
ms.assetid: 94682cba-1f68-416f-af74-99ede81eadc7
keywords:
- INF files WDK device installations
- INF files WDK device installations , creating
- Device setup WDK device installations , INF files
- device installations WDK , INF files
- installing devices WDK , INF files
- Install a driver by using an INF file
ms.date: 04/20/2017
ms.localizationpriority: High
---

# Overview of INF Files

Windows uses setup information (INF) files to install the following components for a device:

-   One or more drivers that support the device.

-   Device-specific configuration or settings to bring the device online.

An INF file is a text file that contains all the information that [device installation components](https://docs.microsoft.com/previous-versions/ff541277(v=vs.85)) used to install a driver. Windows installs drivers using INF files. This information includes the following:

-   Driver name and location
-   Driver version information
-   Registry information

You can use an *INX* file to automatically create an INF file. An INX file is an INF file that contains string variables that represent version information. The Build utility and the [Stampinf](https://docs.microsoft.com/windows-hardware/drivers/devtest/stampinf) tool replace the string variables in INX files with text strings that represent a specific hardware architecture or framework version. For more information about INX files, see [Using INX Files to Create INF Files](https://docs.microsoft.com/windows-hardware/drivers/wdf/using-inx-files-to-create-inf-files).


See [INF File Sections and Directives](inf-file-sections-and-directives.md) for a complete description of INF file format.
