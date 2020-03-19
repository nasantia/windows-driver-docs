---
title: Checking the Oplock State of an IRP_MJ_CLEANUP operation
description: Checking the Oplock State of an IRP_MJ_CLEANUP operation
ms.assetid: 5e078575-cbb8-4460-9986-4c546b8c20be
ms.date: 11/25/2019
ms.localizationpriority: medium
---

# Checking the Oplock State of an IRP_MJ_CLEANUP operation

The following [oplock break](https://docs.microsoft.com/windows-hardware/drivers/ifs/breaking-oplocks) conditions apply only when a *stream* is being closed.

### Conditions for Level 2 and Read request types

- Always break to None. Note that other Level 2 or Read oplocks on the same stream are not affected; only the Level 2 or Read oplock associated with this FILE_OBJECT is broken.

- No acknowledgment is required; the operation proceeds immediately.

### Conditions for Level 1, Batch, Filter, Read-Handle, Read-Write, and Read-Write-Handle request types

- Always break to None.

- No acknowledgment is required; the operation proceeds immediately. Note that any I/O operations (IRPs) waiting for an acknowledgment from a pending break request are completed immediately.
