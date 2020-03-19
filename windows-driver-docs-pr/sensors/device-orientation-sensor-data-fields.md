---
title: Orientation sensor data fields
description: This topic provides information about the data fields that are specific to the orientation sensor.
ms.assetid: 4B1FA56E-6956-4BC9-B929-3D78EF933057
ms.date: 07/20/2018
ms.localizationpriority: medium
---

# Orientation sensor data fields


This topic provides information about the data fields that are specific to the orientation sensor.

The following table shows the data fields. For more information about the types shown in the type column, see the [PROPVARIANT structure](https://go.microsoft.com/fwlink/p/?linkid=313395).

|Property key|Type|Required/Optional|Description/Comments|
|---|---|---|---|
|PKEY_SensorData_QuaternionW|VT_R4|Required|Real coefficient (as opposed to the imaginary portion of the complex number) of rotational axis vector.|
|PKEY_SensorData_QuaternionX|VT_R4|Required|X-component of rotational axis vector.|
|PKEY_SensorData_QuaternionY|VT_R4|Required|Y-component of rotational axis vector.|
|PKEY_SensorData_QuaternionZ|VT_R4|Required|Z-component of rotational axis vector.|
|PKEY_SensorData_MagnetometerAccuracy|VT_UI4|Required|The accuracy of the magnetometer sensor. For more information about valid values, see [MAGNETOMETER_ACCURACY](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorsdef/ne-sensorsdef-magnetometer_accuracy).|
|PKEY_SensorData_DeclinationAngle_Degrees|VT_R4|Optional|Magnetic declination angle used to infer the true north from the earth's magnetic north. If not supported, the class extension will compute this value.|
|PKEY_SensorData_LinearAccelerationX_Gs|VT_R4|Optional|X-axis linear acceleration in g’s|
|PKEY_SensorData_LinearAccelerationY_Gs|VT_R4|Optional|Y-axis linear acceleration in g’s|
|PKEY_SensorData_LinearAccelerationZ_Gs|VT_R4|Optional|Z-axis linear acceleration in g’s|
|PKEY_SensorData_CorrectedAngularVelocityX_DegreesPerSecond|VT_R4|Optional|Gyrometric X-axis velocity, in degrees per second.|
|PKEY_SensorData_CorrectedAngularVelocityY_DegreesPerSecond|VT_R4|Optional|Gyrometric Y-axis velocity, in degrees per second.|
|PKEY_SensorData_CorrectedAngularVelocityZ_DegreesPerSecond|VT_R4|Optional|Gyrometric Z-axis velocity, in degrees per second.|


## Related topics


[MSDN PROPVARIANT structure](https://go.microsoft.com/fwlink/p/?linkid=313395)






