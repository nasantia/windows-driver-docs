---
title: eSIM management on Windows for mobile operators and OEMs
description: eSIM management on Windows for mobile operators and OEMs
ms.assetid: 7D37D297-76FD-46DA-ACC3-73E4BF970524
ms.date: 05/23/2019
ms.localizationpriority: medium
---

# eSIM management on Windows for mobile operators and OEMs

## Mobile operators and OEMs

If you are a mobile operator or OEM and would like to support eSIM management on Windows, follow these steps:

1. Conduct a Hardware Lab Kit (HLK) test run. This ensures modem hardware compatibility with Windows 10 eSIM support. OEMs and ODMs must ensure execution of the following HLK eSIM tests:
    1. Basic eSIM support test cases:
        - [Win6_4.MB.CDMA.Data.TestLowLevelUiccAccess](https://docs.microsoft.com/windows-hardware/test/hlk/testref/f27c8d81-7e2b-49d1-be4c-614bf62f003c)
        - [Win6_4.MB.GSM.Data.TestLowLevelUiccAccess](https://docs.microsoft.com/windows-hardware/test/hlk/testref/104db926-5cc4-47ad-a7d0-ff476b0f57a1)
    2. For Windows 10 devices with both a removable SIM slot and a soldered eUICC:
        - [Win6_4.MB.CDMA.Data.TestSlot](https://docs.microsoft.com/windows-hardware/test/hlk/testref/049a0532-3d58-49aa-ac3d-2a9b8aab24a7) and/or [Win6_4.MB.GSM.Data.TestSlot](https://docs.microsoft.com/windows-hardware/test/hlk/testref/defddebe-cc40-4d6f-9b0c-ca5ca9a1cb4d)
        - [Win6_4.MB.CDMA.Data.TestDeviceCapsEx](https://docs.microsoft.com/windows-hardware/test/hlk/testref/e4ec5199-0841-4864-ac17-b6b71f81cdf3) and/or [Win6_4.MB.GSM.Data.TestDeviceCapsEx](https://docs.microsoft.com/windows-hardware/test/hlk/testref/75c812d5-8c7d-4589-8336-7d72f2feb987)

Windows provides the capability for Mobile Device Management providers to manage eSIM profiles in enterprise use cases. However, Windows does not limit how ecosystem partners might want to offer this to their own partners and/or customers. As such, the eSIM profile management capability can be supported by integrating with the Windows OMA-DM. This makes it possible to remotely manage the eSIM profiles according to company policies.

If you would like to integrate and work with only one MDM provider, contact that provider directly. If you would like to offer eSIM management to customers using different MDM providers, contact an [orchestrator provider](https://www.idemia.com/esim-management-facilitation). Orchestrator providers act as a proxy that handles MDM onboarding as well as mobile operator onboarding. Their [role](https://www.idemia.com/smart-connect-hub) is to make the process as painless and scalable as possible for all parties.

## eSIM management for other audiences

If you are an MDM provider and would like to support eSIM management on Windows, see [How Mobile Device Management Providers support eSIM Management on Windows](https://docs.microsoft.com/windows/client-management/mdm/esim-enterprise-management).

If you are an end user in an organization and would like to use an eSIM for a cellular data connection on your organization-provided device, see [Use an eSIM to get a cellular data connection on your Windows 10 PC](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).