---
title: Gyroscope thresholds
description: This topic provides information about the gyroscope thresholds.
ms.assetid: 68B11108-CA1A-4A49-BC44-4E9FE09955A9
ms.date: 07/20/2018
ms.localizationpriority: medium
---

# Gyroscope thresholds


This topic provides information about the gyroscope thresholds.

The following table shows the default thresholds for the gyroscope. For more information about the types shown in the type column, see the [PROPVARIANT structure](https://go.microsoft.com/fwlink/p/?linkid=313395).

|Property key|Type|Required/Optional|Default value|Description|
|---|---|---|---|---|
|PKEY_SensorData_AngularVelocityX_DegreesPerSecond|VT_R4|Required|0.1f|Minimum amount of change of angular velocity around the x-axis required to reach the threshold, measured in degrees per second.|
|PKEY_SensorData_AngularVelocityY_DegreesPerSecond|VT_R4|Required|0.1f|Minimum amount of change of angular velocity around the y-axis required to reach the threshold, measured in degrees per second.|
|PKEY_SensorData_AngularVelocityZ_DegreesPerSecond|VT_R4|Required|0.1f|Minimum amount of change of angular velocity around the z-axis required to reach the threshold, measured in degrees per second.|

Gyroscope drivers must report a sample reading to the sensors class extension by calling [SensorsCxSensorDataReady](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorscx/nf-sensorscx-sensorscxsensordataready) when either PKEY_SensorData_AngularVelocityX_DegreesPerSecond, PKEY_SensorData_AngularVelocityY_DegreesPerSecond, or PKEY_SensorData_AngularVelocityZ_DegreesPerSecond thresholds are met. Each threshold must be measured per-axis. Drivers must therefore call SensorsCxSensorDataReady whenever the threshold condition is met on any one of the axis.
When PKEY_SensorData_AngularVelocityX_DegreesPerSecond, or PKEY_SensorData_AngularVelocityY_DegreesPerSecond, or PKEY_SensorData_AngularVelocityZ_DegreesPerSecond is set to 0.0f, the driver must report sample readings to the sensors class extension at every interval. This mode is known as *sensor sample streaming*.

Gyroscope drivers must always report one sample reading immediately after the sensors class extension calls the [EvtSensorStart](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorscx/ns-sensorscx-_sensor_controller_config) callback irrespective of the threshold values. This sample is known as the known as initial sample reading.

## Related topics


[PROPVARIANT structure](https://go.microsoft.com/fwlink/p/?linkid=313395)







