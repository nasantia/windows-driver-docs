---
title: PPD-Specific Interface
description: PPD-Specific Interface
ms.assetid: 12d5baa2-4fd4-4eca-84c7-1ee168ee8259
keywords:
- PostScript Printer Driver WDK print , PPD-specific interface
- Pscript WDK print , PPD-specific interface
- IPrintCoreUI2
- PPD files WDK Pscript
- PPD-specific interface WDK Pscript
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# PPD-Specific Interface





The IPrintCoreUI2 COM Interface files. Six of these methods are supported in the [IPrintCorePS2 COM Interface](iprintcoreps2-com-interface.md). This section describes the PPD-specific behavior of these methods.

### IPrintCoreUI2 Interface PPD Methods

[**IPrintCoreUI2::EnumConstrainedOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-enumconstrainedoptions)

[**IPrintCoreUI2::EnumFeatures**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-enumfeatures)

[**IPrintCoreUI2::EnumOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-enumoptions)

[**IPrintCoreUI2::GetOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-getoptions)

[**IPrintCoreUI2::GetFeatureAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-getfeatureattribute)

[**IPrintCoreUI2::GetGlobalAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-getglobalattribute)

[**IPrintCoreUI2::GetOptionAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-getoptionattribute)

[**IPrintCoreUI2::SetOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-setoptions)

[**IPrintCoreUI2::WhyConstrained**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreui2-whyconstrained)

### IPrintCorePS2 Interface PPD Methods

[**IPrintCorePS2::EnumFeatures**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-enumfeatures)

[**IPrintCorePS2::EnumOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-enumoptions)

[**IPrintCorePS2::GetOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-getoptions)

[**IPrintCorePS2::GetFeatureAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-getfeatureattribute)

[**IPrintCorePS2::GetGlobalAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-getglobalattribute)

[**IPrintCorePS2::GetOptionAttribute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintcoreps2-getoptionattribute)

Throughout this section, a reference to any method that is a member of both interfaces applies to both methods. For example, a reference to **GetOptions** applies to **IPrintCoreUI2::GetOptions** as well as to **IPrintCorePS2::GetOptions**.

### PPD Feature Availability

Note that in this section, the phrase "PPD feature is not currently available" means that either the printer does not support the feature, or the feature's non-None/False options are constrained by current installable option settings.

For example, "Duplex feature is not currently available" means either the PPD does not specify the \***Duplex** feature keyword, or the \***Duplex** feature keyword's non-None options are currently constrained by the fact that the duplex unit is not installed.

 

 




