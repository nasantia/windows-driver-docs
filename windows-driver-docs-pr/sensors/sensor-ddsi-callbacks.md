---
title: Sensor DDSI Callbacks
description: The sensor device driver software interface (DDSI) functions represent the interface a sensor driver uses to interact with the class extension.
ms.assetid: 3DB30155-8DBE-4AE9-A0CC-8089DC255E32
ms.date: 07/20/2018
ms.localizationpriority: medium
---

# Sensor DDSI callbacks

The sensor device driver software interface (DDSI) functions represent the interface a sensor driver uses to interact with the class extension. These callbacks are implemented by sensor drivers and called by the class extension. You can find more information about these callbacks in the [_SENSOR_CONTROLLER_CONFIG structure](https://docs.microsoft.com/windows-hardware/drivers/ddi/sensorscx/ns-sensorscx-_sensor_controller_config).

## Callbacks

|Topic|Description|
|---|---|
|EvtSensorDisableWake|Callback to disable wake for the sensor. |
|EvtSensorEnableWake|Callback to enable wake for the sensor.|
|EvtSensorStartStateChangeNotification|Used to start a state change notification.|
|EvtSensorStopStateChangeNotification|Used to stop a state change notification.|
|EvtSensorStart|This callback function starts the sensor based on the default properties specified by the driver, or properties set by the class extension.|
|EvtSensorStop|This callback function stops the sensor.|
|EvtSensorGetSupportedDataFields|This callback function returns a list of data fields supported by the specified sensor.|
|EvtSensorGetProperties|This callback function returns the properties for a given sensor.|
|EvtSensorGetDataFieldProperties|This callback function returns the properties of a given data field associated with a sensor.|
|EvtSensorGetDataInterval|This callback function returns the data interval for a specified sensor.|
|EvtSensorSetDataInterval|This callback function sets the data interval for a specified sensor.|
|EvtSensorGetDataThresholds|This callback function returns the thresholds that are associated with a sensor.|
|EvtSensorSetDataThresholds|This callback function sets the threshold for one or more data fields associated with a sensor.|
|EvtSensorDeviceIoControl|This callback function handles IOCTLs outside of the class extension.|
|EvtSensorSetBatchLatency|This callback function sets the batch latency for a specified sensor.|

