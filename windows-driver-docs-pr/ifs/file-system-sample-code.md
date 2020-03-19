---
title: File system sample code
description: File system sample code
ms.assetid: a64d83c6-d4cd-432d-bc1a-a3ff4656527c
keywords:
- drivers WDK file system
- file system drivers WDK
ms.date: 02/10/2020
ms.localizationpriority: medium
---

# File system sample code

In almost all situations, developing a full file system driver for Windows is not necessary. If you do decide to develop a new file system driver, the [*fastfat* sample](https://docs.microsoft.com/windows-hardware/drivers/samples/file-system-driver-samples) is available for you to use as a model. To learn how to install a file system driver, see [Creating an INF File for a File System Driver](creating-an-inf-file-for-a-file-system-driver.md).

The WDK does not provide conceptual documentation for file system development.

Most file system-related development on Windows involves the creation of a file system filter (or "minifilter") driver that interacts with the system-supplied [Filter Manager](filter-manager-concepts.md).
