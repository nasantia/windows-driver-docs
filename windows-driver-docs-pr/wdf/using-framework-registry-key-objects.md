---
title: Using Framework Registry-Key Objects
description: Using Framework Registry-Key Objects
ms.assetid: 2236b4e1-2e17-4e59-b12e-70fff5fd7513
keywords:
- registry WDK KMDF
- registry-key objects WDK KMDF
- framework-based drivers WDK KMDF , registry
- kernel-mode drivers WDK KMDF , registry
- KMDF WDK , registry
- Kernel-Mode Driver Framework WDK , registry
- keys WDK KMDF
- opening registry keys WDK KMDF
- removing registry keys WDK KMDF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Using Framework Registry-Key Objects


Framework-based drivers access the registry by using *framework registry-key objects*. The registry-key object defines methods that enable your driver to create, open, and close registry keys; add and remove registry values; and read or write the data that is assigned to a registry value.

To open a registry key, your driver must call [**WdfRegistryOpenKey**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryopenkey). If the key does not exist, the driver must call [**WdfRegistryCreateKey**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistrycreatekey), which creates a new key and opens it.

When your driver opens a registry key, the framework creates a registry-key object that represents the opened key and returns an object handle to the driver. The driver must use the object handle to access the key, any subkeys that exist under the key, and any values that exist under the key or its subkeys.

To read the data that is currently assigned to a registry value name, the driver can call one of the following object methods:

<a href="" id="---------wdfregistryquerymemory--------"></a>[**WdfRegistryQueryMemory**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryquerymemory)  
Retrieves the data that is currently assigned to a value name, stores the data in a framework-allocated buffer, and creates a framework memory object to represent the buffer.

<a href="" id="---------wdfregistryquerymultistring--------"></a>[**WdfRegistryQueryMultiString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryquerymultistring)  
Retrieves the string data that is currently assigned to a multi-string-typed value name, creates a framework string object for each string, and adds each string object to an object collection.

<a href="" id="---------wdfregistryquerystring--------"></a>[**WdfRegistryQueryString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryquerystring)  
Retrieves the string data that is currently assigned to a string-typed value name and assigns the string to a specified framework string object.

<a href="" id="---------wdfregistryqueryunicodestring--------"></a>[**WdfRegistryQueryUnicodeString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryqueryunicodestring)  
Retrieves the string data that is currently assigned to a string-typed value name and copies the string to a specified [**UNICODE\_STRING**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfwdm/ns-wudfwdm-_unicode_string) structure.

<a href="" id="---------wdfregistryqueryulong--------"></a>[**WdfRegistryQueryULong**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryqueryulong)  
Retrieves the unsigned long word (REG\_DWORD) data that is currently assigned to a value name and copies the data to a specified location.

<a href="" id="---------wdfregistryqueryvalue--------"></a>[**WdfRegistryQueryValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryqueryvalue)  
Retrieves the data that is currently assigned to a value name and copies the data to a driver-supplied buffer.

To write data to a registry value, the driver can call one of the following methods. If the value name already exists, the operating system updates the value's data.

<a href="" id="---------wdfregistryassignmemory--------"></a>[**WdfRegistryAssignMemory**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignmemory)  
Assigns data that is contained in a memory buffer to a specified value name in the registry.

<a href="" id="---------wdfregistryassignmultistring--------"></a>[**WdfRegistryAssignMultiString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignmultistring)  
Assigns a set of strings to a specified value name in the registry. The strings are contained in a driver-supplied collection of framework string objects.

<a href="" id="---------wdfregistryassignstring--------"></a>[**WdfRegistryAssignString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignstring)  
Assigns a string to a specified value name in the registry. The string is contained in a framework string object.

<a href="" id="---------wdfregistryassignunicodestring--------"></a>[**WdfRegistryAssignUnicodeString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignunicodestring)  
Assigns a specified Unicode string to a specified value name in the registry.

<a href="" id="---------wdfregistryassignulong--------"></a>[**WdfRegistryAssignULong**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignulong)  
Assigns a specified unsigned long word value to a specified value name in the registry.

<a href="" id="---------wdfregistryassignvalue--------"></a>[**WdfRegistryAssignValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryassignvalue)  
Assigns the contents of a driver-supplied data buffer to a specified value name in the registry.

To remove a registry value, the driver must call [**WdfRegistryRemoveValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryremovevalue). To remove a key, the driver must call [**WdfRegistryRemoveKey**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryremovekey).

To obtain WDM information about the registry, a driver can call [**WdfRegistryWdmGetHandle**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistrywdmgethandle), which returns a WDM handle to the registry key that a framework registry-key object represents.

After your driver has finished accessing a registry key, it must call [**WdfRegistryClose**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfregistry/nf-wdfregistry-wdfregistryclose) or [**WdfObjectDelete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfobject/nf-wdfobject-wdfobjectdelete) to close the key and delete the registry-key object.

 

 





