---
title: Percent of wi-fi connection failures, from the top 95 percent of device and access-point pairs 
description: The measure aggregates telemetry from a 7-day sliding window into a percentage of instances where a device fails to connect to an access point
ms.topic: article
ms.date: 05/20/2019
ms.localizationpriority: medium
---

# Percent of wi-fi connection failures, from the top 95 percent of device and access-point pairs 

## Description

A Wi-Fi Access Point (AP) is a networking hardware that allows other Wi-Fi enabled devices to connect to a wireless local area network (WLAN). When users cannot connect to an AP, their machines display a *Can’t connect to access point* error message and will not have access to the WLAN or Wi-Fi.

## Measure attributes

|Attribute|Value|
|----|----|
|**Audience**|Targeted HWIDs and CHIDs|
|**Time period**|7 days|
|**Measurement criteria**|Aggregation of instances |
|**Minimum instances**|3,000|
|**Passing criteria**|<= 2% of Instances have connection failures to APs |
|**Measure ID**|14642524|

## Calculation

1. The measure aggregates telemetry from a 7-day sliding window into a **percentage of instances where a device fails to connect to an AP**

   a. An instance is a pairing between a device and unique AP; per device, the measure aggregates every attempted connection to a unique AP.

   b. The measure does not aggregate any device–AP pairs if their signal strength is below 50%.

   c. If a device–AP pair’s connection rate falls within the lower 5th percentile of device-AP pairs, the measure will not aggregate it.

2. A connection failure is counted as “100” and a connection success is counted as “0”

### Final calculation

*Connection failure rate of device–AP pairs = average(all instances)*