---
title: Percent of machines where the driver install process completes successfully
description: The measure aggregates telemetry from a 30-day sliding window into a Percentage of Machines that have Successfully Installed the Driver
ms.topic: article
ms.date: 05/20/2019
ms.localizationpriority: medium
---

# Percent of machines where the driver install process completes successfully

## Description

When a driver fails to install correctly, the targeted component can lose functionality and prevent the user from accessing the component’s features. The user must troubleshoot the issue to regain functionality. A list of PNP error codes is located on [Device Manager Problem Codes](https://docs.microsoft.com/windows-hardware/drivers/install/device-manager-error-messages) and on [Windows Support](https://support.microsoft.com/help/310123/error-codes-in-device-manager-in-windows).

## Measure attributes

|Attribute|Value|
|----|----|
|**Audience**|Expanded|
|**Time period**|30 day sliding window|
|**Measurement criteria**|Aggregation of machines|
|**Minimum population**|100 machines|
|**Passing criteria**|>= 95% of machines install the driver successfully|
|**Measure ID**|10042840|

## Calculation

1. The measure aggregates telemetry from a 30-day sliding window into a **Percentage of Machines that have Successfully Installed the Driver**.
2. *Successful Installs= Count(machines with successful PNP events)*
3. *Total Installs= Count(machines that started the driver install process)*

### Final Calculation

*PNP Success Rate= Succesful Installs / Total Installs*
